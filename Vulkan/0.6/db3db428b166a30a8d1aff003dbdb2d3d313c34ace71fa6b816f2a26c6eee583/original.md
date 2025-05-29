High-level wrapper for VkBindImageMemoryInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryInfo.html)

```julia
struct BindImageMemoryInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image::Vulkan.Image`
  * `memory::Vulkan.DeviceMemory`
  * `memory_offset::UInt64`
