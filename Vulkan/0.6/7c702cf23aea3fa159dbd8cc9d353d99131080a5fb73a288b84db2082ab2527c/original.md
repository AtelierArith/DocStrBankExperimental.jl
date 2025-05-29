Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FORMAT_NOT_SUPPORTED`
  * `ERROR_IMAGE_USAGE_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_OPERATION_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_FORMAT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PICTURE_LAYOUT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_CODEC_NOT_SUPPORTED_KHR`

Arguments:

  * `physical_device::PhysicalDevice`
  * `image_format_info::PhysicalDeviceImageFormatInfo2`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceImageFormatProperties2.html)

```julia
get_physical_device_image_format_properties_2(
    physical_device,
    image_format_info::Vulkan.PhysicalDeviceImageFormatInfo2,
    next_types::Type...
) -> ResultTypes.Result{Vulkan.ImageFormatProperties2, Vulkan.VulkanError}

```
