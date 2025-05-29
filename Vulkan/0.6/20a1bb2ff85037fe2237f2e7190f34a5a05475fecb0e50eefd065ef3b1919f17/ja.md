VkSparseBufferMemoryBindInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseBufferMemoryBindInfo.html)

```julia
struct _SparseBufferMemoryBindInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSparseBufferMemoryBindInfo`
  * `deps::Vector{Any}`
  * `buffer::Vulkan.Buffer`
