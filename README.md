# ros-python

## Create a ROS Package
Reference: http://wiki.ros.org/ROS/Tutorials/CreatingPackage

$ cd ros-python/src
$ catkin_create_pkg beginner_tutorials std_msgs rospy roscpp

### This is an example, do not try to run this
### catkin_create_pkg <package_name> [depend1] [depend2] [depend3]

$ source /opt/ros/melodic/setup.bash

$ cd ros-python
$ catkin_make

$ source devel/setup.bash
$ echo $ROS_PACKAGE_PATH

$ . ros-python/devel/setup.bash
$ rospack depends1 beginner_tutorials
$ roscd beginner_tutorials
$ cat package.xml
$ rospack depends1 rospy
$ rospack depends beginner_tutorials

## Writing Publisher:
$ roscd beginner_tutorials
$ mkdir scripts
$ cd scripts
$ wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/rospy_tutorials/001_talker_listener/talker.py
$ chmod +x talker.py

### In begineer_toutorial/CMakeLists.txt add below lines:
catkin_install_python(PROGRAMS scripts/talker.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

## Writing the Subscriber:
$ roscd beginner_tutorials/scripts/
$ wget https://raw.github.com/ros/ros_tutorials/kinetic-devel/rospy_tutorials/001_talker_listener/listener.py
$ chmod +x listener.py

### In begineer_toutorial/CMakeLists.txt add below lines:
catkin_install_python(PROGRAMS scripts/talker.py scripts/listener.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

## Build workspace:
$ cd ros-python <catkin_ws git repo>
$ catkin_make

## Run publisher and Subscriber

#### Open terminal and run
$ roscore

#### Open another terminal and run
$ cd ros-python <catkin_ws git repo>
$ source ./devel/setup.bash
$ rosrun beginner_tutorials talker      (C++)
$ rosrun beginner_tutorials talker.py   (Python)

#### Open another terminal and run
$ cd ros-python <catkin_ws git repo>
$ source ./devel/setup.bash
$ rosrun beginner_tutorials listener     (C++)
$ rosrun beginner_tutorials listener.py  (Python)

#### Open another terminal and run
$ rostopic list


## Kill roscore: 
$ killall -9 roscore
$ killall -9 rosmaster