拡張: VK*NVX*image*view*handle

引数:

  * `image_view::ImageView`
  * `descriptor_type::DescriptorType`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `sampler::Sampler`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewHandleInfoNVX.html)

```julia
_ImageViewHandleInfoNVX(
    image_view,
    descriptor_type::Vulkan.DescriptorType;
    next,
    sampler
) -> Vulkan._ImageViewHandleInfoNVX

```
