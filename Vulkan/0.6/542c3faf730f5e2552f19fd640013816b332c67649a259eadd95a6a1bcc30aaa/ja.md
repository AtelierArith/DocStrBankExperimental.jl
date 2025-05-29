VkSparseImageMemoryBindの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBind.html)

```julia
struct _SparseImageMemoryBind <: Vulkan.VulkanStruct{false}
```

  * `vks::VulkanCore.LibVulkan.VkSparseImageMemoryBind`
  * `memory::Union{Ptr{Nothing}, Vulkan.DeviceMemory}`
