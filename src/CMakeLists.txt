add_executable(starultra main.cpp)
target_link_libraries(
  starultra
  PRIVATE project_options
          project_warnings
          CONAN_PKG::docopt.cpp
          CONAN_PKG::fmt
          CONAN_PKG::spdlog)

download_project(PROJ           msufsort
                 GIT_REPOSITORY https://github.com/michaelmaniscalco/msufsort.git
                 GIT_TAG        master
)

add_subdirectory(${msufsort_SOURCE_DIR} ${msufsort_BINARY_DIR})

include_directories(${msufsort_SOURCE_DIR}/src/library)
