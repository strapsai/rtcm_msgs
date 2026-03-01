Content created by Yaoyu's AI assistant. Use with care.

# RTCM Messages

`rtcm_msgs` is a standard ROS 2 package containing message definitions for RTCM (Radio Technical Commission for Maritime Services) data. This package provides a standardized way to represent raw RTCM correction streams, which are essential for high-precision GNSS/GPS positioning (RTK).

## Overview

In the STRAPS/DTC ecosystem, `rtcm_msgs` is used to transport GNSS correction data from base stations or NTRIP casters to the robot's onboard GNSS receivers. This allows for centimeter-level positioning accuracy during field operations.

## Message Definitions

- `Message.msg`: Represents a single RTCM message packet, containing the raw byte payload and the standard ROS 2 header.

## Repository Structure

- `msg/`: ROS 2 message definition files (.msg).
- `CMakeLists.txt` & `package.xml`: ROS 2 build and dependency configuration.

## Prerequisites

- **ROS 2 Humble / Rolling**
- **Dependencies**:
  - `builtin_interfaces`
  - `std_msgs`

## Installation

1. Clone the repository into your ROS 2 workspace:
   ```bash
   cd ~/ros2_ws/src
   git clone https://github.com/strapsai/rtcm_msgs.git
   ```

2. Build the package:
   ```bash
   cd ~/ros2_ws
   colcon build --packages-select rtcm_msgs
   ```

## Usage

In your GNSS driver or correction broadcaster:

### Python Example
```python
from rtcm_msgs.msg import Message
msg = Message()
msg.message = b'\xd3\x00\x13...' # raw RTCM bytes
# ... publish msg ...
```

### C++ Example
```cpp
#include <rtcm_msgs/msg/message.hpp>
auto msg = rtcm_msgs::msg::Message();
msg.message = {0xd3, 0x00, 0x13, ...}; // raw RTCM bytes
// ... publish msg ...
```

## License

This project is licensed under the BSD License - see the [LICENSE](LICENSE) file for details.
