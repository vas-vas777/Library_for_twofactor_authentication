cmake_minimum_required(VERSION 3.26)
project(sdk_for_token)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_PREFIX_PATH "/usr/lib/x86_64-linux-gnu/cmake/Qt6/Qt6Config.cmake")
find_package(OpenSSL)
find_package(Boost)
if (NOT MSVC)
    link_libraries(${OPENSSL_LIBRARIES})
else ()
endif ()
find_package(Qt6 COMPONENTS
        Core
        Gui
        Widgets
        SerialPort
        REQUIRED)

add_library(sdk_for_token SHARED
        gost_3410_2012.cpp
        gost_3411_2012_calc.c
        SerialQt.cpp)

target_link_libraries(sdk_for_token PRIVATE
        Qt6::Core
        Qt6::Gui
        Qt6::Widgets
        Qt6::SerialPort
)