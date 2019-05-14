# Cardboard Arena

## Abstract
A Gazebo world out of cardboard for rapid and comprehensive testing of mobile robotic systems in simulation.

## Alvar tags launch file parameters
+ marker_size – marker size in cm
+ cam_image_topic – topic of image data
+ cam_info_topic – topic of calibration data
+ output_frame – the frame which the calculated pose of the marker refers to
+ max_frequency – maximum frequency, with which the whole algorithm is running

## Run
### To just visualize the simulated world in Gazebo:

- Clone this repository into a ROS catkin workspace
- To launch Gazebo and the ar_tag_arena.world : `roslaunch cardboard_arena ar_tag_arena.launch`

### To run a full demo in combination with a simulated robot and Alvar Tags:

+ Clone following repositories to a catkin workspace (for example ~/catkin_ws/src):

  This Gazebo simulated environment:  
  `$ git clone https://github.com/rfzeg/cardboard_arena.git`  
  A URDF robot model for simulation:  
  `$ git clone https://github.com/rfzeg/dumpster.git`  
  Install the ar_track_alvar for detecting and tracking AR Tags:  
  `$ sudo apt-get install ros-kinetic-ar-track-alvar`  
 
+ Build and source your workspace :

  `$ cd ~/catkin_ws`  
  `$ catkin_make`  
  `$ source devel/setup.bash`
    
+ Run the project by executing in separated terminal instances:

  `$ roslaunch cardboard_arena ar_tag_arena.launch`  
  `$ roslaunch dumpster spawn_dumpster.launch`  

  `$ roslaunch cardboard_arena ar_track.launch cam_image_topic:=/dumpster/camera1/image_raw cam_info_topic:=/dumpster/camera1/camera_info output_frame:=camera`  

  Then unpause the simulation.

## Testing and debugging

To actually read the poses of the AR tags, you can echo the ar_pose_marker topic:  
`$ rostopic echo /ar_pose_marker -n1`  
The -n1 flag prints the topic exactly once.  


**Disclaimer**  
The ar_tag_arena world was inspired by the real world practice and competition areas used during my attendance to the **ROS Summer School 2018** at the **Aachen University of Applied Science** in Germany.

