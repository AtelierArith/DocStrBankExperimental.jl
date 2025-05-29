Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FORMAT_NOT_SUPPORTED`

Arguments:

  * `physical_device::PhysicalDevice`
  * `format::Format`
  * `type::ImageType`
  * `tiling::ImageTiling`
  * `usage::ImageUsageFlag`
  * `flags::ImageCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceImageFormatProperties.html)

```julia
_get_physical_device_image_format_properties(
    physical_device,
    format::Vulkan.Format,
    type::Vulkan.ImageType,
    tiling::Vulkan.ImageTiling,
    usage::Vulkan.ImageUsageFlag;
    flags
) -> ResultTypes.Result{Vulkan._ImageFormatProperties, Vulkan.VulkanError}

```
