Intermediate wrapper for VkCopyImageInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageInfo2.html)

```julia
struct _CopyImageInfo2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyImageInfo2`
  * `deps::Vector{Any}`
  * `src_image::Vulkan.Image`
  * `dst_image::Vulkan.Image`
