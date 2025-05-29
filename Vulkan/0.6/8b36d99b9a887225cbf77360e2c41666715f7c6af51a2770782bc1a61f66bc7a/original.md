High-level wrapper for VkDependencyInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDependencyInfo.html)

```julia
struct DependencyInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `dependency_flags::Vulkan.DependencyFlag`
  * `memory_barriers::Vector{Vulkan.MemoryBarrier2}`
  * `buffer_memory_barriers::Vector{Vulkan.BufferMemoryBarrier2}`
  * `image_memory_barriers::Vector{Vulkan.ImageMemoryBarrier2}`
