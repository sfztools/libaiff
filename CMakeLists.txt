cmake_minimum_required(VERSION 3.7)

project(libaiff)

include(CheckLibraryExists)
check_library_exists("m" "sin" "" HAVE_LIBM)

add_library(aiff STATIC
  "libaiff/libaiff.h"
  "private.h"
  "aifx.c"
  "extended.c"
  "float32.c"
  "g711.c"
  "iff.c"
  "libaiff.c"
  "lpcm.c"
  "pascal.c")
target_include_directories(aiff PUBLIC ".")
if (HAVE_LIBM)
  target_link_libraries(aiff PRIVATE "m")
endif()
