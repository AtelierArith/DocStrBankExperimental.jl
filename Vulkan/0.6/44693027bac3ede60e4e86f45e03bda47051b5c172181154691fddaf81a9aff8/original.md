Intermediate wrapper for VkResolveImageInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkResolveImageInfo2.html)

```julia
struct _ResolveImageInfo2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkResolveImageInfo2`
  * `deps::Vector{Any}`
  * `src_image::Vulkan.Image`
  * `dst_image::Vulkan.Image`
