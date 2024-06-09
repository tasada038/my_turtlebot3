cmake_minimum_required(VERSION 3.5)
project(mb3_gazebo)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(control_msgs REQUIRED)
find_package(rclcpp REQUIRED)
find_package(rclcpp_action REQUIRED)
find_package(std_msgs REQUIRED)
find_package(geometry_msgs REQUIRED)

set(BASE_LIBS
  ament_cmake
  geometry_msgs
  rclcpp
  rclcpp_action
  control_msgs
  sensor_msgs
  std_msgs
)


install(DIRECTORY
  launch
  worlds
  DESTINATION share/${PROJECT_NAME}/
)

## Install
install(TARGETS
  DESTINATION lib/${PROJECT_NAME}
)

ament_package()