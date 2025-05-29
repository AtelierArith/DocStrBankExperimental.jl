High-level wrapper for VkSparseBufferMemoryBindInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseBufferMemoryBindInfo.html)

```julia
struct SparseBufferMemoryBindInfo <: Vulkan.HighLevelStruct
```

  * `buffer::Vulkan.Buffer`
  * `binds::Vector{Vulkan.SparseMemoryBind}`
