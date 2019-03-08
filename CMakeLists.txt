cmake_minimum_required(VERSION 3.13)
project(VulkanFoo)
set(CMAKE_CXX_STANDARD 14)

if (DEFINED ENV{VULKAN_SDK})
    message(STATUS "Vulkan SDK: $ENV{VULKAN_SDK}")
else ()
    message(STATUS "No Vulkan SDK found")
endif ()

find_package(Vulkan REQUIRED)

file(GLOB SOURCES
        ${CMAKE_CURRENT_SOURCE_DIR}/src/*.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/*.hpp
        ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp
        ${CMAKE_CURRENT_SOURCE_DIR}/src/**/*.h
        ${CMAKE_CURRENT_SOURCE_DIR}/src/**/*.hpp
        ${CMAKE_CURRENT_SOURCE_DIR}/src/**/*.cpp)

add_executable(VulkanFoo ${SOURCES})

target_compile_definitions(VulkanFoo PRIVATE VK_USE_PLATFORM_WIND32_KHR)
target_link_libraries(VulkanFoo Vulkan::Vulkan)