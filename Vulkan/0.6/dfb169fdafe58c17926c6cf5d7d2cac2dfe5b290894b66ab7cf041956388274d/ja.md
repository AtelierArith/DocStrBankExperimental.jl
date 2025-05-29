引数:

  * `image::Image`
  * `view_type::ImageViewType`
  * `format::Format`
  * `components::_ComponentMapping`
  * `subresource_range::_ImageSubresourceRange`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::ImageViewCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewCreateInfo.html)

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
