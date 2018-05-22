cmake_minimum_required(VERSION 2.8.3)
project(aeolus-io)
set(PROJECT_VERSION 2.5.8)



add_library(${CMAKE_PROJECT_NAME} SHARED ${CMAKE_PROJECT_NAME}.cpp)

add_executable(gee_main_${CMAKE_PROJECT_NAME} main.cpp)

configure_file(${CMAKE_PROJECT_NAME}.pc.in ${CMAKE_PROJECT_NAME}.pc)

set_target_properties(${CMAKE_PROJECT_NAME}
    PROPERTIES   VERSION ${PROJECT_VERSION}
)

install(TARGETS gee_main_${CMAKE_PROJECT_NAME} ${CMAKE_PROJECT_NAME}
        RUNTIME DESTINATION bin
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
)

install(FILES
	${CMAKE_CURRENT_LIST_DIR}/${CMAKE_PROJECT_NAME}.h
    DESTINATION include/${CMAKE_PROJECT_NAME}
)

install(FILES
	${CMAKE_BINARY_DIR}/${CMAKE_PROJECT_NAME}.pc
    DESTINATION share/pkgconfig
)
