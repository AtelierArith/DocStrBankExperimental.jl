High-level wrapper for VkImageViewHandleInfoNVX.

Extension: VK_NVX_image_view_handle

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewHandleInfoNVX.html)

```julia
struct ImageViewHandleInfoNVX <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image_view::Vulkan.ImageView`
  * `descriptor_type::Vulkan.DescriptorType`
  * `sampler::Union{Ptr{Nothing}, Vulkan.Sampler}`
