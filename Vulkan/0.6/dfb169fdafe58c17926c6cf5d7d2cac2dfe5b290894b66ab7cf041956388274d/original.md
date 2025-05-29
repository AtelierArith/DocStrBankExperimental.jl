Arguments:

  * `image::Image`
  * `view_type::ImageViewType`
  * `format::Format`
  * `components::_ComponentMapping`
  * `subresource_range::_ImageSubresourceRange`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::ImageViewCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewCreateInfo.html)

```julia
_ImageViewCreateInfo(
    image,
    view_type::Vulkan.ImageViewType,
    format::Vulkan.Format,
    components::Vulkan._ComponentMapping,
    subresource_range::Vulkan._ImageSubresourceRange;
    next,
    flags
) -> Vulkan._ImageViewCreateInfo

```
