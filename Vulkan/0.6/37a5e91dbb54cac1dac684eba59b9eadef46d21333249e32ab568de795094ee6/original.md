High-level wrapper for VkSparseImageMemoryBind.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBind.html)

```julia
struct SparseImageMemoryBind <: Vulkan.HighLevelStruct
```

  * `subresource::Vulkan.ImageSubresource`
  * `offset::Vulkan.Offset3D`
  * `extent::Vulkan.Extent3D`
  * `memory::Union{Ptr{Nothing}, Vulkan.DeviceMemory}`
  * `memory_offset::UInt64`
  * `flags::Vulkan.SparseMemoryBindFlag`
