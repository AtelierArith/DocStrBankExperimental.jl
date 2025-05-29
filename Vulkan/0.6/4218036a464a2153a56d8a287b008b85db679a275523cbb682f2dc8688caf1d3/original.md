Extension: VK_KHR_video_queue

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_VIDEO_STD_VERSION_NOT_SUPPORTED_KHR`

Arguments:

  * `device::Device`
  * `create_info::_VideoSessionCreateInfoKHR`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionKHR.html)

```julia
_create_video_session_khr(
    device,
    create_info::Vulkan._VideoSessionCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.VideoSessionKHR, Vulkan.VulkanError}

```
