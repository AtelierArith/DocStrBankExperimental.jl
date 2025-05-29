Extension: VK_NVX_image_view_handle

Arguments:

  * `image_view::ImageView`
  * `descriptor_type::DescriptorType`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `sampler::Sampler`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewHandleInfoNVX.html)

```julia
_ImageViewHandleInfoNVX(
    image_view,
    descriptor_type::Vulkan.DescriptorType;
    next,
    sampler
) -> Vulkan._ImageViewHandleInfoNVX

```
