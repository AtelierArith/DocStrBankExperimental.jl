返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FORMAT_NOT_SUPPORTED`

引数:

  * `physical_device::PhysicalDevice`
  * `format::Format`
  * `type::ImageType`
  * `tiling::ImageTiling`
  * `usage::ImageUsageFlag`
  * `flags::ImageCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceImageFormatProperties.html)

```julia
get_physical_device_image_format_properties(
    physical_device,
    format::Vulkan.Format,
    type::Vulkan.ImageType,
    tiling::Vulkan.ImageTiling,
    usage::Vulkan.ImageUsageFlag;
    flags
) -> ResultTypes.Result{Vulkan.ImageFormatProperties, Vulkan.VulkanError}

```
