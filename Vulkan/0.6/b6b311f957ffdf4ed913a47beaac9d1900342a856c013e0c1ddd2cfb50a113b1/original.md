Arguments:

  * `device::Device`
  * `image::Image`
  * `view_type::ImageViewType`
  * `format::Format`
  * `components::_ComponentMapping`
  * `subresource_range::_ImageSubresourceRange`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::ImageViewCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateImageView.html)

```julia
ImageView(
    device,
    image,
    view_type::Vulkan.ImageViewType,
    format::Vulkan.Format,
    components::Vulkan._ComponentMapping,
    subresource_range::Vulkan._ImageSubresourceRange;
    allocator,
    next,
    flags
) -> Vulkan.ImageView

```
