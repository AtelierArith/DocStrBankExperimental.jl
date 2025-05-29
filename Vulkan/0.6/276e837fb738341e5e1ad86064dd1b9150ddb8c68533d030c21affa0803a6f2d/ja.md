VkDedicatedAllocationMemoryAllocateInfoNVの中間ラッパー。

拡張: VK*NV*dedicated_allocation

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDedicatedAllocationMemoryAllocateInfoNV.html)

```julia
struct _DedicatedAllocationMemoryAllocateInfoNV <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkDedicatedAllocationMemoryAllocateInfoNV`
  * `deps::Vector{Any}`
  * `image::Union{Ptr{Nothing}, Vulkan.Image}`
  * `buffer::Union{Ptr{Nothing}, Vulkan.Buffer}`
