# It's important to not include the wrong math.h here.
set(CMAKE_INCLUDE_CURRENT_DIR OFF)

set(PXR_PREFIX pxr/base)
set(PXR_PACKAGE arch)

set(PLATFORM_LIBS ${M_LIB})
if(WIN32)
    set(PLATFORM_LIBS Ws2_32.lib Dbghelp.lib ${PLATFORM_LIBS})
endif()

pxr_shared_library(arch
    LIBRARIES
        ${CMAKE_THREAD_LIBS_INIT}
        ${CMAKE_DL_LIBS}
        ${PLATFORM_LIBS}

    INCLUDE_DIRS
        ${Boost_INCLUDE_DIRS}

    PUBLIC_CLASSES
        attributes
        daemon
        debugger
        demangle
        env
        error
        errno
        fileSystem
        function
        hash
        library
        mallocHook
        nap
        regex
        stackTrace
        symbols
        systemInfo
        threads
        timing
        vsnprintf

    PUBLIC_HEADERS
        align.h
        api.h
        buildMode.h
        defines.h
        export.h
        functionLite.h
        hints.h
        inttypes.h
        math.h
        pragmas.h

    PRIVATE_HEADERS
        testArchAbi.h
        testArchUtil.h

    CPPFILES
        assumptions.cpp
        initConfig.cpp
)

pxr_build_test_shared_lib(testArchAbiPlugin
    CPPFILES
        testenv/testArchAbiPlugin.cpp
)
pxr_build_test(testArchAbi
    LIBRARIES
        arch
    CPPFILES
        testenv/testArchAbi.cpp
)
pxr_build_test(testArchAttributes
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testAttributes.cpp
    )
pxr_build_test(testArchDemangle
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testDemangle.cpp
)
pxr_build_test(testArchError
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testArchUtil.cpp
        testenv/testError.cpp
)
pxr_build_test(testArchErrno
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testErrno.cpp
)
pxr_build_test(testArchFileSystem
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testFileSystem.cpp
)
pxr_build_test(testArchFunction
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testFunction.cpp
)
pxr_build_test(testArchStackTrace
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testArchUtil.cpp
        testenv/testStackTrace.cpp
)
pxr_build_test(testArchSymbols
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testSymbols.cpp
)
pxr_build_test(testArchSystemInfo
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testSystemInfo.cpp
)
pxr_build_test(testArchThreads
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testThreads.cpp
)
pxr_build_test(testArchTiming
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testTiming.cpp
)
pxr_build_test(testArchVsnprintf
    LIBRARIES
        arch
        ${CMAKE_DL_LIBS}
    CPPFILES
        testenv/testVsnprintf.cpp
)

pxr_register_test(testArchAbi
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchAbi"
)
pxr_register_test(testArchAttributes
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchAttributes"
)
pxr_register_test(testArchDemangle
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchDemangle"
)
pxr_register_test(testArchError
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchError"
)
pxr_register_test(testArchErrno
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchErrno"
)
pxr_register_test(testArchFileSystem
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchFileSystem"
)
pxr_register_test(testArchFunction
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchFunction"
)
pxr_register_test(testArchStackTrace
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchStackTrace"
)
pxr_register_test(testArchSymbols
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchSymbols"
)
pxr_register_test(testArchSystemInfo
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchSystemInfo"
)
pxr_register_test(testArchTiming
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchTiming"
)
pxr_register_test(testArchThreads
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchThreads"
)
pxr_register_test(testArchVsnprintf
    COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testArchVsnprintf"
)
