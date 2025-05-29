Extension: VK_NVX_image_view_handle

Arguments:

  * `image_view::ImageView`
  * `descriptor_type::DescriptorType`
  * `next::Any`: defaults to `C_NULL`
  * `sampler::Sampler`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewHandleInfoNVX.html)

```julia
ImageViewHandleInfoNVX(
    image_view::Vulkan.ImageView,
    descriptor_type::Vulkan.DescriptorType;
    next,
    sampler
) -> Vulkan.ImageViewHandleInfoNVX

```
