返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `image::Image`
  * `view_type::ImageViewType`
  * `format::Format`
  * `components::_ComponentMapping`
  * `subresource_range::_ImageSubresourceRange`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::ImageViewCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateImageView.html)

```julia
_create_image_view(
    device,
    image,
    view_type::Vulkan.ImageViewType,
    format::Vulkan.Format,
    components::Vulkan._ComponentMapping,
    subresource_range::Vulkan._ImageSubresourceRange;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.ImageView, Vulkan.VulkanError}

```
