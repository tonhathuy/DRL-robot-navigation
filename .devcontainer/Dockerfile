FROM nvcr.io/nvidia/pytorch:21.10-py3

# Timezone
RUN echo 'Asia/Ho_Chi_Minh' > /etc/timezone && \
    ln -s /usr/share/zoneinfo/Etc/UTC /etc/localtime  

# Essential packages
RUN apt-get update && apt-get install -y --no-install-recommends\
    build-essential curl 

# ROS
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu focal main" > /etc/apt/sources.list.d/ros-latest.list'
RUN curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -


RUN apt-get update && apt-get install -y --fix-missing --no-install-recommends\
    ros-noetic-desktop-full 
RUN echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc && . ~/.bashrc

RUN pip install empy catkin_pkg rosdep rosinstall rosinstall-generator wstool
RUN rosdep init && rosdep update

# Source the ROS setup file
RUN echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ~/.bashrc
