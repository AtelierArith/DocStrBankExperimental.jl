Extension: VK_KHR_video_queue

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_VIDEO_PROFILE_OPERATION_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_FORMAT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PICTURE_LAYOUT_NOT_SUPPORTED_KHR`
  * `ERROR_VIDEO_PROFILE_CODEC_NOT_SUPPORTED_KHR`

Arguments:

  * `physical_device::PhysicalDevice`
  * `video_profile::VideoProfileInfoKHR`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceVideoCapabilitiesKHR.html)

```julia
get_physical_device_video_capabilities_khr(
    physical_device,
    video_profile::Vulkan.VideoProfileInfoKHR,
    next_types::Type...
) -> ResultTypes.Result{Vulkan.VideoCapabilitiesKHR, Vulkan.VulkanError}

```
