VkPhysicalDevicePropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProperties.html)

```julia
struct PhysicalDeviceProperties <: Vulkan.HighLevelStruct
```

  * `api_version::VersionNumber`
  * `driver_version::VersionNumber`
  * `vendor_id::UInt32`
  * `device_id::UInt32`
  * `device_type::Vulkan.PhysicalDeviceType`
  * `device_name::String`
  * `pipeline_cache_uuid::NTuple{16, UInt8}`
  * `limits::Vulkan.PhysicalDeviceLimits`
  * `sparse_properties::Vulkan.PhysicalDeviceSparseProperties`
