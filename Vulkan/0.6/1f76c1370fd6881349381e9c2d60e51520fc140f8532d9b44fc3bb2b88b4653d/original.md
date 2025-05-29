Intermediate wrapper for VkImageViewHandleInfoNVX.

Extension: VK_NVX_image_view_handle

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewHandleInfoNVX.html)

```julia
struct _ImageViewHandleInfoNVX <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkImageViewHandleInfoNVX`
  * `deps::Vector{Any}`
  * `image_view::Vulkan.ImageView`
  * `sampler::Union{Ptr{Nothing}, Vulkan.Sampler}`
