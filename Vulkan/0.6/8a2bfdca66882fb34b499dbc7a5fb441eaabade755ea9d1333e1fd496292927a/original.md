Extension: VK_EXT_device_fault

Arguments:

  * `header_size::UInt32`
  * `header_version::DeviceFaultVendorBinaryHeaderVersionEXT`
  * `vendor_id::UInt32`
  * `device_id::UInt32`
  * `driver_version::VersionNumber`
  * `pipeline_cache_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `application_name_offset::UInt32`
  * `application_version::VersionNumber`
  * `engine_name_offset::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultVendorBinaryHeaderVersionOneEXT.html)

```julia
_DeviceFaultVendorBinaryHeaderVersionOneEXT(
    header_size::Integer,
    header_version::Vulkan.DeviceFaultVendorBinaryHeaderVersionEXT,
    vendor_id::Integer,
    device_id::Integer,
    driver_version::VersionNumber,
    pipeline_cache_uuid::NTuple{16, UInt8},
    application_name_offset::Integer,
    application_version::VersionNumber,
    engine_name_offset::Integer
) -> Vulkan._DeviceFaultVendorBinaryHeaderVersionOneEXT

```
