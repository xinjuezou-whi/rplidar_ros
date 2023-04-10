# WHI exteded RPLIDAR ROS package
This package forked from the offical repository with the extended functionality of scan range screening

## Range definition of laser frame
The range's start is defined aligning with the axis -x, and increases clockwise up to 360 degrees:
![image](https://user-images.githubusercontent.com/72239958/230850302-8ff34f75-b9c4-4fd8-a4f7-069e2522ffdf.png)


## Range screening
Added argument "screen_off" controls whether to screen off the data withing specified range(0-360 degrees). The intended screening off range can be set by params: screened_begin and screened_end. Let's say that degrees from 180 degrees to 270 degrees should be screened off since the data within this range are interferenced with the mast behind the LiDAR. Then we can set the param "screened_begin" as 180 and "screened_end" as 270 in launch file "rplidar.launch", the argument can be set to true directly in launch file, or specified in command line while launching, like this:
```
roslaunch rplidar_ros rplidar.launch screen_off:=true
```

![screened_off](https://user-images.githubusercontent.com/72239958/230855140-6cb6972c-cfcc-491d-9884-7224d6b9fbf4.png)

<br>

> ***Bellowing contents are the original of RPLIDAR ROS package:***

RPLIDAR ROS package
=====================================================================

ROS node and test application for RPLIDAR

Visit following Website for more details about RPLIDAR:

rplidar roswiki: http://wiki.ros.org/rplidar

rplidar HomePage:   http://www.slamtec.com/en/Lidar

rplidar SDK: https://github.com/Slamtec/rplidar_sdk

rplidar Tutorial:  https://github.com/robopeak/rplidar_ros/wiki

How to build rplidar ros package
=====================================================================
    1) Clone this project to your catkin's workspace src folder
    2) Running catkin_make to build rplidarNode and rplidarNodeClient

How to run rplidar ros package
=====================================================================
There're two ways to run rplidar ros package

I. Run rplidar node and view in the rviz
------------------------------------------------------------
```bash
roslaunch rplidar_ros view_rplidar.launch (for RPLIDAR A1/A2)
```
```bash
roslaunch rplidar_ros view_rplidar_a3.launch (for RPLIDAR A3)
``` 
```bash
roslaunch rplidar_ros view_rplidar_s1.launch (for RPLIDAR S1)
``` 
```bash 
roslaunch rplidar_ros view_rplidar_s2.launch (for RPLIDAR S2)
``` 
```bash 
roslaunch rplidar_ros view_rplidar_s2e.launch (for RPLIDAR S2E)
``` 
```bash
roslaunch rplidar_ros view_rplidar_t1.launch (for SLAMTEC LPX T Serials)  
``` 
You should see rplidar's scan result in the rviz.

II. Run rplidar node and view using test application
------------------------------------------------------------
```bash
roslaunch rplidar_ros rplidar.launch (for RPLIDAR A1/A2)
```
```bash
roslaunch rplidar_ros rplidar_a3.launch (for RPLIDAR A3)
```
```bash 
roslaunch rplidar_ros rplidar_s1.launch (for RPLIDAR S1)
```
```bash 
roslaunch rplidar_ros rplidar_s2.launch (for RPLIDAR S2)
```
```bash
roslaunch rplidar_ros rplidar_s2e.launch (for RPLIDAR S2E)
```
```bash 
roslaunch rplidar_ros rplidar_t1.launch (for SLAMTEC LPX T Serials)  
```
rosrun rplidar_ros rplidarNodeClient

You should see rplidar's scan result in the console

Notice: the different is serial_baudrate between A1/A2<115200> , A3/S1<256000> and S2<1000000>

RPLidar frame
=====================================================================
RPLidar frame must be broadcasted according to picture shown in rplidar-frame.png
