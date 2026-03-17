qt_add_library(quickshell-river-classic STATIC
	output.cpp
	tag.cpp
	manager.cpp
	qml.cpp
)

qt_add_qml_module(quickshell-river-classic
	URI Quickshell.RiverClassic
	VERSION 0.1
)

install_qml_module(quickshell-river-classic)

wl_proto(wlp-river-classic-ipc river-status-unstable-v1.xml "${CMAKE_CURRENT_SOURCE_DIR}")

target_link_libraries(quickshell-river-classic PRIVATE
	Qt::Core
	Qt::Gui
	Qt::GuiPrivate
	Qt::WaylandClient
	Qt::WaylandClientPrivate
	Wayland::Client
	wlp-river-classic-ipc
)

target_link_libraries(quickshell PRIVATE quickshell-river-classicplugin)
