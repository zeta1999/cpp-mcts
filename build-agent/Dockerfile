
FROM debian:buster

# General Tools
RUN apt-get update && apt-get install -y llvm clang clang-tidy clang-format libc++-7-dev libc++abi-dev libgl1-mesa-dev git curl unzip python3 python3-pip xsltproc
# Conan C++ package manager
RUN pip3 install conan
# SonarQube C++ build wrapper
RUN curl https://sonarcloud.io/static/cpp/build-wrapper-linux-x86.zip -O && unzip build-wrapper-linux-x86.zip -d /opt && rm build-wrapper-linux-x86.zip
# CMake (cmake from apt is too old)
RUN cd /tmp && curl https://github.com/Kitware/CMake/releases/download/v3.15.6/cmake-3.15.6.tar.gz -O -L && \
    tar -xf cmake-3.15.6.tar.gz && cd cmake-3.15.6 && CC=clang CXX=clang++ ./bootstrap && make install && rm -rf /tmp/cmake*

ENV PATH="/opt/build-wrapper-linux-x86:${PATH}"
