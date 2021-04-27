FROM ubuntu:20.04

RUN apt-get update
RUN apt-get upgrade -y

# Workaround for an installation issue with Ubuntu 20.04
RUN DEBIAN_FRONTEND="noninteractive" apt-get install tzdata -y

RUN apt-get install wget curl build-essential cmake gcc g++ git python3 python3-pip -y

RUN pip3 install --upgrade pip
RUN pip3 install tensorflow
RUN pip3 install tensorflow_datasets
RUN pip3 install sklearn
RUN pip3 install pandas
RUN pip3 install jupyterlab
RUN pip3 install matplotlib
RUN pip3 install imutils

# Install OpenCV
RUN apt-get -y install build-essential checkinstall cmake pkg-config yasm
RUN apt-get -y install git gfortran
RUN apt-get -y install libjpeg8-dev libpng-dev

RUN apt-get -y install software-properties-common
RUN add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"
RUN apt-get -y update

RUN apt-get -y install libjasper1
RUN apt-get -y install libtiff-dev

RUN apt-get -y install libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev
RUN apt-get -y install libxine2-dev libv4l-dev
RUN cd /usr/include/linux && ln -s -f ../libv4l1-videodev.h videodev.h

RUN apt-get -y install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev
RUN apt-get -y install libgtk2.0-dev libtbb-dev qt5-default
RUN apt-get -y install libatlas-base-dev
RUN apt-get -y install libfaac-dev libmp3lame-dev libtheora-dev
RUN apt-get -y install libvorbis-dev libxvidcore-dev
RUN apt-get -y install libopencore-amrnb-dev libopencore-amrwb-dev
RUN apt-get -y install libavresample-dev
RUN apt-get -y install x264 v4l-utils

RUN apt-get install libjpeg-dev libopenexr-dev libwebp-dev -y

RUN apt-get install ffmpeg -y

RUN apt-get -y install tesseract-ocr

RUN \	
    cd / \
    &&\	
    git clone https://github.com/opencv/opencv.git --single-branch 4.4.0\
    &&\	
    mv 4.4.0 opencv\
    &&\	
    cd opencv\
    &&\	
    mkdir build\
    &&\	
    cd build\
    &&\	
    cmake \
        -D CMAKE_BUILD_TYPE=RELEASE \
        -D BUILD_TESTS=OFF \
        -D BUILD_PERF_TESTS=OFF \
        -D BUILD_opencv_python_tests=OFF \
        -D WITH_FFMPEG=ON \
        -D WITH_TBB=ON \
        -D WITH_V4L=ON \
        -D WITH_QT=ON \
        -D WITH_OPENGL=ON \
        -D WITH_GSTREAMER=ON \
        ..\
    &&\
    make\
    &&\	
    make install