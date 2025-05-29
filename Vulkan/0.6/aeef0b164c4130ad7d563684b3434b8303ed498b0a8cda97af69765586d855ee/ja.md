VkSparseImageMemoryBindInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBindInfo.html)

```julia
struct _SparseImageMemoryBindInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSparseImageMemoryBindInfo`
  * `deps::Vector{Any}`
  * `image::Vulkan.Image`
