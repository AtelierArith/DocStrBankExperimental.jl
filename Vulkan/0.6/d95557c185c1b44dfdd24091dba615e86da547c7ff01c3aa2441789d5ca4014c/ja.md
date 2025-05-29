VkDeviceMemoryReportCallbackDataEXTの高レベルラッパー。

拡張: VK*EXT*device*memory*report

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceMemoryReportCallbackDataEXT.html)

```julia
struct DeviceMemoryReportCallbackDataEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `type::Vulkan.DeviceMemoryReportEventTypeEXT`
  * `memory_object_id::UInt64`
  * `size::UInt64`
  * `object_type::Vulkan.ObjectType`
  * `object_handle::UInt64`
  * `heap_index::UInt32`
