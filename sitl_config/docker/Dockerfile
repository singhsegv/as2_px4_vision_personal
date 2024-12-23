FROM osrf/ros:humble-desktop

# Clone px4 autopilot
WORKDIR /root/
RUN git clone https://github.com/PX4/PX4-Autopilot.git -b v1.14.3 --recursive

WORKDIR /root/PX4-Autopilot/

# Upgrading the system
RUN apt update && apt upgrade -y
RUN apt-get install wget -y

# Install dependencies
RUN ./Tools/setup/ubuntu.sh --no-nuttx
RUN make px4_sitl

ADD PX4-gazebo-models/worlds/baylands.sdf /root/PX4-Autopilot/Tools/simulation/gz/worlds/
ADD PX4-gazebo-models/models/mono_cam /root/PX4-Autopilot/Tools/simulation/gz/models/mono_cam
ADD PX4-gazebo-models/models/x500_mono_cam /root/PX4-Autopilot/Tools/simulation/gz/models/x500_mono_cam
