
configure_file(version.h.in ${CMAKE_CURRENT_BINARY_DIR}/version.h)
include_directories(${CMAKE_CURRENT_BINARY_DIR})

set(NEOVIM_QT_SOURCES util.cpp neovimconnector.cpp neovimconnectorhelper.cpp function.cpp msgpackrequest.cpp msgpackiodevice.cpp auto/neovimapi0.cpp auto/neovimapi1.cpp auto/neovimapi2.cpp auto/neovimapi3.cpp auto/neovimapi4.cpp)
if(WIN32)
  list(APPEND NEOVIM_QT_SOURCES stdinreader.cpp)
endif()

add_library(neovim-qt STATIC ${NEOVIM_QT_SOURCES})
target_link_libraries(neovim-qt Qt5::Network ${MSGPACK_LIBRARIES})

add_subdirectory(gui)
