拡張機能: VK*NVX*image*view*handle

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_UNKNOWN`

引数:

  * `device::Device`
  * `image_view::ImageView`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageViewAddressNVX.html)

```julia
get_image_view_address_nvx(
    device,
    image_view
) -> ResultTypes.Result{Vulkan.ImageViewAddressPropertiesNVX, Vulkan.VulkanError}

```
