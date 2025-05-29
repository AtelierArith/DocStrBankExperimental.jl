戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FORMAT_NOT_SUPPORTED`
  * `ERROR_IMAGE_USAGE_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_OPERATION_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_FORMAT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PICTURE_LAYOUT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_CODEC_NOT_SUPPORTED_KHR`

引数:

  * `physical_device::PhysicalDevice`
  * `image_format_info::PhysicalDeviceImageFormatInfo2`
  * `next_types::Type...`: `next` チェーンの一部として初期化し、含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceImageFormatProperties2.html)

```julia
get_physical_device_image_format_properties_2(
    physical_device,
    image_format_info::Vulkan.PhysicalDeviceImageFormatInfo2,
    next_types::Type...
) -> ResultTypes.Result{Vulkan.ImageFormatProperties2, Vulkan.VulkanError}

```
