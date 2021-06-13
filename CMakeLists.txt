cmake_minimum_required (VERSION 3.0)

PROJECT(image_video)

#set (CMAKE_CXX_STANDARD 11)
#Set the compiler
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_BUILD_TYPE Release)
set( EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

IF(EXISTS ${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
    include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
    conan_basic_setup()
ENDIF()

# Requires OpenCV
FIND_PACKAGE( OpenCV 4.0.0 REQUIRED )
MESSAGE("OpenCV version : ${OpenCV_VERSION}")

#Bring the headers
include_directories(${PROJECT_SOURCE_DIR}/include)

ADD_EXECUTABLE( sample1 ${PROJECT_SOURCE_DIR}/src/sample1.cpp )
TARGET_LINK_LIBRARIES( sample1 ${OpenCV_LIBS} ${CONAN_LIBS} -lprotobuf ) 


ADD_EXECUTABLE( sample2 ${PROJECT_SOURCE_DIR}/src/sample2.cpp )
TARGET_LINK_LIBRARIES( sample2 ${OpenCV_LIBS} ${CONAN_LIBS} -lprotobuf)

ADD_EXECUTABLE( sample3 ${PROJECT_SOURCE_DIR}/src/sample3.cpp )
TARGET_LINK_LIBRARIES( sample3 ${OpenCV_LIBS} ${CONAN_LIBS} -lprotobuf)

ADD_EXECUTABLE( ${PROJECT_NAME} ${PROJECT_SOURCE_DIR}/src/main.cpp )
TARGET_LINK_LIBRARIES( ${PROJECT_NAME} ${OpenCV_LIBS} ${CONAN_LIBS} -lprotobuf)
