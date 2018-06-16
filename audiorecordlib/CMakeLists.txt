# Sets the minimum version of CMake required to build the native
# library. You should either keep the default value or only pass a
# value of 3.4.0 or lower.

cmake_minimum_required(VERSION 3.4.1)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/../jniLibs/audiorecordlib/${ANDROID_ABI})
# Creates and names a library, sets it as either STATIC
# or SHARED, and provides the relative paths to its source code.
# You can define multiple libraries, and CMake builds it for you.
# Gradle automatically packages shared libraries with your APK.

add_library( # Sets the name of the library.
             mp3lame

             # Sets the library as a shared library.
             SHARED

             # Provides a relative path to your source file(s).
             # Associated headers in the same location as their source
             # file are automatically included.
             src/main/cpp/lame_utils.cpp
             src/main/cpp/libmp3lame/lame.c
             src/main/cpp/libmp3lame/util.c
             src/main/cpp/libmp3lame/psymodel.c
             src/main/cpp/libmp3lame/fft.c
             src/main/cpp/libmp3lame/tables.c
             src/main/cpp/libmp3lame/encoder.c
             src/main/cpp/libmp3lame/newmdct.c
             src/main/cpp/libmp3lame/quantize_pvt.c
             src/main/cpp/libmp3lame/reservoir.c
             src/main/cpp/libmp3lame/bitstream.c
             src/main/cpp/libmp3lame/VbrTag.c
             src/main/cpp/libmp3lame/version.c
             src/main/cpp/libmp3lame/takehiro.c
             src/main/cpp/libmp3lame/quantize.c
             src/main/cpp/libmp3lame/vbrquantize.c
             src/main/cpp/libmp3lame/gain_analysis.c
             src/main/cpp/libmp3lame/id3tag.c
             src/main/cpp/libmp3lame/set_get.c
             src/main/cpp/libmp3lame/presets.c )

include_directories(src/main/cpp src/main/cpp/include)

add_definitions(-DSTDC_HEADERS -DHAVE_MEMCPY -DHAVE_STRCHR)

# Searches for a specified prebuilt library and stores the path as a
# variable. Because system libraries are included in the search path by
# default, you only need to specify the name of the public NDK library
# you want to add. CMake verifies that the library exists before
# completing its build.

find_library( # Sets the name of the path variable.
              log-lib

              # Specifies the name of the NDK library that
              # you want CMake to locate.
              log )

# Specifies libraries CMake should link to your target library. You
# can link multiple libraries, such as libraries you define in the
# build script, prebuilt third-party libraries, or system libraries.

target_link_libraries( # Specifies the target library.
                       mp3lame

                       # Links the target library to the log library
                       # included in the NDK.
                       ${log-lib} )
