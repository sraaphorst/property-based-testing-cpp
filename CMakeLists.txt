cmake_minimum_required(VERSION 2.8.8)

project(PropertyBasedTesting C CXX)

enable_testing()
find_package(GTest REQUIRED)

message(STATUS "CMake version   : " ${CMAKE_SYSTEM_VERSION})
message(STATUS "Compiler        : " ${CMAKE_CXX_COMPILER})
message(STATUS "Operating System: " ${CMAKE_SYSTEM})

set(RAPIDCHECK_PATH rapidcheck)
set(RAPIDCHECK_INCLUDE_DIRS ${RAPIDCHECK_PATH}/include ${RAPIDCHECK_PATH}/extras/gtest/include)
add_subdirectory(${RAPIDCHECK_PATH})

if("${CMAKE_CXX_COMPILER_ID}" STREQUAL "GNU" OR "${CMAKE_CXX_COMPILER_ID}" STREQUAL "Clang")
  set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")
  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/build)
endif()

set(CMAKE_CXX_STANDARD 17)

include_directories(SYSTEM ${GTEST_INCLUDE_DIRS})
include_directories(SYSTEM ${RAPIDCHECK_INCLUDE_DIRS})

add_subdirectory(musicplayer)
add_subdirectory(shadows-of-the-knight)
add_subdirectory(string-contains)