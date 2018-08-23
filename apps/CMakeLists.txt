cmake_minimum_required(VERSION 2.8.11)

# Set recognition option
option(EnableRecognition "EnableRecognition" OFF)
if(EnableRecognition)
  add_definitions(-DHAS_RECOGNITION)
endif()

# Configure dependencies
set (CMAKE_MODULE_PATH "${CMAKE_CURRENT_SOURCE_DIR}/../cmake")
include(XP_lib_helper)
include(XP_custom_3rdparty_helper)
include(XP_sys_3rdparty_helper)

# Use C++ 11
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
add_definitions(-mtune=native)


find_package(catkin REQUIRED
            COMPONENTS
            roscpp
            image_transport
            cv_bridge
            rosbag
            tf
            dynamic_reconfigure
            nav_msgs
            std_srvs
	    message_generation	
)


include_directories(
  ${catkin_INCLUDE_DIRS}
)

message(STATUS "catkin_INCLUDE_DIRS= ${catkin_INCLUDE_DIRS}")


# Add apps that uses libXP.so
#add_subdirectory(app_tracking)
add_subdirectory(xp_sensor_logger)
#add_subdirectory(cam_calibration)

