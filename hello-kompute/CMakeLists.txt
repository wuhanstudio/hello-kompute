cmake_minimum_required(VERSION 3.20)
project(hello-kompute)

set(CMAKE_CXX_STANDARD 14)

# Options
option(KOMPUTE_OPT_GIT_TAG "The tag of the repo to use for the example" v0.9.0)

include(FetchContent)
FetchContent_Declare(kompute GIT_REPOSITORY https://github.com/KomputeProject/kompute.git
    GIT_TAG ${KOMPUTE_OPT_GIT_TAG})
FetchContent_MakeAvailable(kompute)
include_directories(${kompute_SOURCE_DIR}/src/include)

# Setting up main example code
add_executable(hello-kompute src/main.cpp)
target_link_libraries(hello-kompute PRIVATE kompute::kompute)
