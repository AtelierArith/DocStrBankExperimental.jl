High-level wrapper for VkBufferCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferCreateInfo.html)

```julia
struct BufferCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.BufferCreateFlag`
  * `size::UInt64`
  * `usage::Vulkan.BufferUsageFlag`
  * `sharing_mode::Vulkan.SharingMode`
  * `queue_family_indices::Vector{UInt32}`
