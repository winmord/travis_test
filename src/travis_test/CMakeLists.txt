cmake_minimum_required(VERSION 3.0.0)
project(travis_test C CXX)

set(CMAKE_CXX_STANDARD 17)
if(MSVC)
    add_definitions(-D_SCL_SECURE_NO_WARNINGS /wd4251 /wd4275 /wd4003 /wd4005 /wd4503 /wd4290 )
endif()

include_directories(${CONAN_INCLUDE_DIRS})
target_include_directories(test PRIVATE ${travis_test_SOURCE_DIR}/include)

set(SOURCE_FILES
	include/travis_test/foo.hpp
	src/main.cpp
	)
	
source_group(TREE ${PROJECT_SOURCE_DIR} FILES ${SOURCE_FILES})
	
add_executable(travis_test ${SOURCE_FILES})
target_link_libraries(travis_test ${CONAN_LIBS})
