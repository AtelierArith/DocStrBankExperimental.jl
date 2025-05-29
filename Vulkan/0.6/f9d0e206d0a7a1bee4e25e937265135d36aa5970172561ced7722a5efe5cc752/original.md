High-level wrapper for VkMemoryGetFdInfoKHR.

Extension: VK_KHR_external_memory_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryGetFdInfoKHR.html)

```julia
struct MemoryGetFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory::Vulkan.DeviceMemory`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
