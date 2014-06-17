cmake_minimum_required(VERSION 2.6)
project(googletests-travisci)

# Locate GTest
ADD_SUBDIRECTORY (gtest-1.7.0)
enable_testing()
include_directories(${gtest_SOURCE_DIR}/include ${gtest_SOURCE_DIR})

find_package (Threads REQUIRED)

# Link runTests with what we want to test and the GTest and pthread library
add_executable(runTests tests.cpp)
target_link_libraries(runTests gtest gtest_main ${CMAKE_THREAD_LIBS_INIT})
add_test( runTests runTests )
