Intermediate wrapper for VkCopyBufferToImageInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferToImageInfo2.html)

```julia
struct _CopyBufferToImageInfo2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyBufferToImageInfo2`
  * `deps::Vector{Any}`
  * `src_buffer::Vulkan.Buffer`
  * `dst_image::Vulkan.Image`
