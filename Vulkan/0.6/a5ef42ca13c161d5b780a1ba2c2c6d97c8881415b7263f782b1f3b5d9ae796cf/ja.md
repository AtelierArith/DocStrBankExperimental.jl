引数:

  * `device::Device`
  * `image::Image`
  * `view_type::ImageViewType`
  * `format::Format`
  * `components::ComponentMapping`
  * `subresource_range::ImageSubresourceRange`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::ImageViewCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateImageView.html)

```julia
ImageView(
    device,
    image,
    view_type::Vulkan.ImageViewType,
    format::Vulkan.Format,
    components::Vulkan.ComponentMapping,
    subresource_range::Vulkan.ImageSubresourceRange;
    allocator,
    next,
    flags
) -> Vulkan.ImageView

```
