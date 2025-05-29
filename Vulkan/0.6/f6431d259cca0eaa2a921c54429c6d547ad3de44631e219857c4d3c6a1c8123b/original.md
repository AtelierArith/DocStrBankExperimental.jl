Arguments:

  * `image::Image`
  * `view_type::ImageViewType`
  * `format::Format`
  * `components::ComponentMapping`
  * `subresource_range::ImageSubresourceRange`
  * `next::Any`: defaults to `C_NULL`
  * `flags::ImageViewCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewCreateInfo.html)

```julia
ImageViewCreateInfo(
    image::Vulkan.Image,
    view_type::Vulkan.ImageViewType,
    format::Vulkan.Format,
    components::Vulkan.ComponentMapping,
    subresource_range::Vulkan.ImageSubresourceRange;
    next,
    flags
) -> Vulkan.ImageViewCreateInfo

```
