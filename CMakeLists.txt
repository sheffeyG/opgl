# CMake 最低版本号要求
cmake_minimum_required (VERSION 2.8)

# 项目信息
project (opgl)

# 查找当前目录下的所有源文件
# 并将名称保存到 DIR_SRCS 变量
# aux_source_directory(./src/test/ DIR_SRCS)

# add_executable(test ${DIR_SRCS})


find_package(OpenGL REQUIRED)
add_library(glad glad/src/glad.c)
target_include_directories(glad  PUBLIC glad/include)

set (CMAKE_CXX_LINK_EXECUTABLE "${CMAKE_CXX_LINK_EXECUTABLE} -ldl")
set( CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/build)

# 指定生成目标
add_executable(main src/main.cpp)
target_link_libraries(main glfw ${GL_LIBRARY} glad)