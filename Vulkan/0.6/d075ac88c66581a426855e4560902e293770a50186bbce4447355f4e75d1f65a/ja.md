VkDeviceFaultVendorBinaryHeaderVersionOneEXTの高レベルラッパー。

拡張: VK*EXT*device_fault

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultVendorBinaryHeaderVersionOneEXT.html)

```julia
struct DeviceFaultVendorBinaryHeaderVersionOneEXT <: Vulkan.HighLevelStruct
```

  * `header_size::UInt32`
  * `header_version::Vulkan.DeviceFaultVendorBinaryHeaderVersionEXT`
  * `vendor_id::UInt32`
  * `device_id::UInt32`
  * `driver_version::VersionNumber`
  * `pipeline_cache_uuid::NTuple{16, UInt8}`
  * `application_name_offset::UInt32`
  * `application_version::VersionNumber`
  * `engine_name_offset::UInt32`
