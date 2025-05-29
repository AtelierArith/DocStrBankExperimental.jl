VkMemoryDedicatedAllocateInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryDedicatedAllocateInfo.html)

```julia
struct _MemoryDedicatedAllocateInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkMemoryDedicatedAllocateInfo`
  * `deps::Vector{Any}`
  * `image::Union{Ptr{Nothing}, Vulkan.Image}`
  * `buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
