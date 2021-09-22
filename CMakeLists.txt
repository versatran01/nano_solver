cmake_minimum_required(VERSION 3.15)
project(nano_solver)

set(CMAKE_CXX_STANDARD 17)

find_package(fmt REQUIRED)
find_package(glog REQUIRED)
find_package(Eigen3 REQUIRED)
find_package(GTest REQUIRED)

add_library(${PROJECT_NAME} src/solver.cpp)
target_include_directories(${PROJECT_NAME} PUBLIC src)
target_link_libraries(${PROJECT_NAME} PUBLIC fmt::fmt glog::glog Eigen3::Eigen)

add_executable(${PROJECT_NAME}_test src/solver_test.cpp)
target_link_libraries(${PROJECT_NAME}_test PUBLIC ${PROJECT_NAME} GTest::GTest
                                                  GTest::Main)
