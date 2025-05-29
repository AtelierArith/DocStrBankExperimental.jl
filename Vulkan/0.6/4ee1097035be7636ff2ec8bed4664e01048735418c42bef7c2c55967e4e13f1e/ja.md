VkPhysicalDeviceGroupPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceGroupProperties.html)

```julia
struct PhysicalDeviceGroupProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `physical_device_count::UInt32`
  * `physical_devices::NTuple{32, Vulkan.PhysicalDevice}`
  * `subset_allocation::Bool`
