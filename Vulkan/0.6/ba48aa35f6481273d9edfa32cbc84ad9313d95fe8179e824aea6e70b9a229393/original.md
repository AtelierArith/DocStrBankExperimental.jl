Intermediate wrapper for VkImageMemoryBarrier.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageMemoryBarrier.html)

```julia
struct _ImageMemoryBarrier <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkImageMemoryBarrier`
  * `deps::Vector{Any}`
  * `image::Vulkan.Image`
