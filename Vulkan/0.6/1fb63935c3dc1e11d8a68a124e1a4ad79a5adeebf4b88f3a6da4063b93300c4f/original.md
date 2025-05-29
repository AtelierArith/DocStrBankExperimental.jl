Intermediate wrapper for VkCopyImageToBufferInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageToBufferInfo2.html)

```julia
struct _CopyImageToBufferInfo2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyImageToBufferInfo2`
  * `deps::Vector{Any}`
  * `src_image::Vulkan.Image`
  * `dst_buffer::Vulkan.Buffer`
