High-level wrapper for VkPhysicalDeviceExternalBufferInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceExternalBufferInfo.html)

```julia
struct PhysicalDeviceExternalBufferInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.BufferCreateFlag`
  * `usage::Vulkan.BufferUsageFlag`
  * `handle_type::Vulkan.ExternalMemoryHandleTypeFlag`
