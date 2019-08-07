
cmake_minimum_required (VERSION 3.15)

project (9cc)

enable_language (C)

if (NOT CMAKE_RUNTIME_OUTPUT_DIRECTORY)
    set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
endif ()
if (NOT CMAKE_LIBRARY_OUTPUT_DIRECTORY)
    set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
endif ()
if (NOT CMAKE_ARCHIVE_OUTPUT_DIRECTORY)
    set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)
endif ()

list (INSERT CMAKE_MODULE_PATH 0 ${CMAKE_BINARY_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/CMake)


add_executable (${PROJECT_NAME})
target_compile_features (${PROJECT_NAME} PRIVATE c_std_11)
target_compile_options (${PROJECT_NAME} PRIVATE -Wall)

target_sources (${PROJECT_NAME}
                PRIVATE gen_ir.c
                        gen_x86.c
                        irdump.c
                        liveness.c
                        main.c
                        opt.c
                        parse.c
                        preprocess.c
                        regalloc.c
                        sema.c
                        token.c
                        util.c
                        util_test.c)

