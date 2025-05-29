拡張: VK*KHR*video_queue

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_IMAGE_USAGE_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_OPERATION_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_FORMAT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PICTURE_LAYOUT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_CODEC_NOT_SUPPORTED_KHR`

引数:

  * `physical_device::PhysicalDevice`
  * `video_format_info::PhysicalDeviceVideoFormatInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceVideoFormatPropertiesKHR.html)

```julia
get_physical_device_video_format_properties_khr(
    physical_device,
    video_format_info::Vulkan.PhysicalDeviceVideoFormatInfoKHR
) -> ResultTypes.Result{Vector{Vulkan.VideoFormatPropertiesKHR}, Vulkan.VulkanError}

```
