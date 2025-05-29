High-level wrapper for VkBindVideoSessionMemoryInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindVideoSessionMemoryInfoKHR.html)

```julia
struct BindVideoSessionMemoryInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory_bind_index::UInt32`
  * `memory::Vulkan.DeviceMemory`
  * `memory_offset::UInt64`
  * `memory_size::UInt64`
