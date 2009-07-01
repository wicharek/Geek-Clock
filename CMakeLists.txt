project(geek-clock)

set(geekclock_SRCS
    geekclock.cpp)

# Find the required Libaries
find_package(KDE4 REQUIRED)
include(KDE4Defaults)
 
add_definitions (${QT_DEFINITIONS} ${KDE4_DEFINITIONS})
include_directories(
   ${CMAKE_SOURCE_DIR}
   ${CMAKE_BINARY_DIR}
   ${KDE4_INCLUDES}
   )
   

kde4_add_ui_files(geekclock_SRCS clockConfig.ui )
kde4_add_plugin(plasma_applet_geekclock ${geekclock_SRCS})
target_link_libraries(plasma_applet_geekclock ${KDE4_PLASMA_LIBS} plasmaclock ${KDE4_KIO_LIBS})

install(TARGETS plasma_applet_geekclock DESTINATION ${PLUGIN_INSTALL_DIR})
install(FILES plasma-applet-geekclock.desktop DESTINATION ${SERVICES_INSTALL_DIR})
install(FILES geekclock.svgz DESTINATION ${DATA_INSTALL_DIR}/desktoptheme/default/widgets/)
