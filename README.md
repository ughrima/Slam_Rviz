# SSL SLAM 

This repository contains all the necessary files, configurations, and instructions to set up and run a SLAM (Simultaneous Localization and Mapping) system using your custom bag file (`sample.bag`). The repository is structured to integrate seamlessly with the existing `ssl_slam` framework and is customized for data recorded with a LIDAR 515 sensor.

## Repository Structure

```
catkin_ws/
├── frames.pdf
├── frames.gv
└── src/
    ├── ssl_slam/
    │   ├── bags/
    │   │   ├── sample.bag
    │   │   └── l515_test.bag
    │   ├── img/
    │   ├── include/
    │   │   └── <header files>
    │   ├── launch/
    │   │   ├── <launch files>
    │   │   ├── depth_to_laserscan.launch (custom)
    │   ├── rviz/
    │   │   ├── <rviz files>
    │   │   └── slam_config_no_tf.rviz (custom)
    │   ├── scripts/
    │   │   ├── camera_info_publisher.py (custom)
    │   ├── src/
    │   │   └── <nodes>
    │   ├── CMakeLists.txt
    │   ├── LICENSE
    │   ├── package.xml
    │   └── README.md
    └── CMakeLists.txt
```

## Dependencies

To run the SLAM system, you need to install the following dependencies:

- **ROS (Robot Operating System)**: [Installation Guide](http://wiki.ros.org/ROS/Installation)
- `ssl_slam` package and its dependencies
- Any other dependencies required by `ssl_slam`

For reference, you can check the dependencies listed in the [original ssl_slam repository](https://github.com/wh200720041/ssl_slam).

## Setup Instructions

1. **Clone the Repository:**

    ```sh
    git clone <your-repo-url>
    cd catkin_ws
    ```

2. **Build the Workspace:**

    ```sh
    catkin_make
    ```

3. **Source the Setup File:**

    ```sh
    source ~/catkin_ws/devel/setup.bash
    ```

## Running the SLAM System

### Using  Custom Bag File

To run the SLAM system with your custom `sample.bag` file. This was recorded using L515 sensor. :

```sh
source ~/catkin_ws/devel/setup.bash
roslaunch ssl_slam depth_to_laserscan.launch
```


### Using the Provided Bag File

To run the SLAM system with the provided `l515_test.bag` file. This was provided in the repository that was followed for reference :

```sh
source ~/catkin_ws/devel/setup.bash
roslaunch ssl_slam ssl_slam.launch
```

## Custom Files Explained

### `depth_to_laserscan.launch`
This launch file is customized to process the `sample.bag` file. It configures the SLAM system to use the LIDAR 515 sensor data recorded in `sample.bag`.

### `camera_info_publisher.py`
This script publishes the camera information for the custom bag file. It ensures that the SLAM system receives the necessary camera calibration data.

### `slam_config_no_tf.rviz`
This RViz configuration file is tailored to visualize the SLAM process without relying on static transformations (`tf`). It helps in visualizing the SLAM data effectively in RViz.

## File Types in ssl_slam and Their Purpose

### ROS Launch Files
Launch files (`.launch`) are XML files that describe the nodes to be executed, their configurations, and parameters. They simplify the process of starting multiple nodes and setting up the entire SLAM system.

### ROS Nodes
Nodes are the executable files written in C++ or Python that perform various tasks in the ROS ecosystem. In this repository, nodes handle the processing of sensor data, SLAM computations, and communication between different components.

### RViz Files
RViz configuration files (`.rviz`) define the visualization settings for the RViz tool. They specify how the sensor data, maps, and other SLAM-related information should be displayed for better understanding and analysis.

## Issues 

### Current Issue
SLAM runs successfully with the provided `l515_test.bag` file but fails to run properly with the `sample.bag` file.
