set(SOURCES
    hlslAttributes.cpp
    hlslParseHelper.cpp
    hlslScanContext.cpp
    hlslOpMap.cpp
    hlslTokenStream.cpp
    hlslGrammar.cpp
    hlslParseables.cpp)

set(HEADERS
    hlslAttributes.h
    hlslParseHelper.h
    hlslTokens.h
    hlslScanContext.h
    hlslOpMap.h
    hlslTokenStream.h
    hlslGrammar.h
    hlslParseables.h)

add_library(HLSL ${LIB_TYPE} ${SOURCES} ${HEADERS})
set_property(TARGET HLSL PROPERTY FOLDER hlsl)
set_property(TARGET HLSL PROPERTY POSITION_INDEPENDENT_CODE ON)

if(WIN32 AND BUILD_SHARED_LIBS)
    set_target_properties(HLSL PROPERTIES PREFIX "")
endif()

if(WIN32)
    source_group("Source" FILES ${SOURCES} ${HEADERS})
endif(WIN32)

if(ENABLE_GLSLANG_INSTALL)
    install(TARGETS HLSL
            ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR})
endif(ENABLE_GLSLANG_INSTALL)
