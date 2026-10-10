if(NOT CONFIG_TLK_FLASHDB)
    return()
endif()

set(FLASHDB_DIR "${CMAKE_CURRENT_SOURCE_DIR}/repo")
target_sources(${TARGET_NAME} PRIVATE
    ${FLASHDB_DIR}/src/fdb_file.c
    ${FLASHDB_DIR}/src/fdb_kvdb.c
    ${FLASHDB_DIR}/src/fdb_utils.c
    ${FLASHDB_DIR}/src/fdb.c
    ${FLASHDB_DIR}/port/fal/src/fal_flash.c
    ${FLASHDB_DIR}/port/fal/src/fal_partition.c
    ${FLASHDB_DIR}/port/fal/src/fal.c
)

target_include_directories(${TARGET_NAME} PRIVATE
    ${FLASHDB_DIR}/inc
    ${FLASHDB_DIR}/port/fal/inc
)

# These warnings are expected
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wno-error=format-truncation -Wno-error=cast-qual -Wno-error=unused-parameter" CACHE STRING "" FORCE)
