Extension: VK_NVX_image_view_handle

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_UNKNOWN`

Arguments:

  * `device::Device`
  * `image_view::ImageView`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageViewAddressNVX.html)

```julia
_get_image_view_address_nvx(
    device,
    image_view
) -> ResultTypes.Result{Vulkan._ImageViewAddressPropertiesNVX, Vulkan.VulkanError}

```
