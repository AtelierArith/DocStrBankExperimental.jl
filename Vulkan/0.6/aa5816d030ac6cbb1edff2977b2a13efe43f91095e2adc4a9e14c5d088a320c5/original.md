High-level wrapper for VkSparseImageOpaqueMemoryBindInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageOpaqueMemoryBindInfo.html)

```julia
struct SparseImageOpaqueMemoryBindInfo <: Vulkan.HighLevelStruct
```

  * `image::Vulkan.Image`
  * `binds::Vector{Vulkan.SparseMemoryBind}`
