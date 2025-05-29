VkPhysicalDeviceIDPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceIDProperties.html)

```julia
struct PhysicalDeviceIDProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `device_uuid::NTuple{16, UInt8}`
  * `driver_uuid::NTuple{16, UInt8}`
  * `device_luid::NTuple{8, UInt8}`
  * `device_node_mask::UInt32`
  * `device_luid_valid::Bool`
