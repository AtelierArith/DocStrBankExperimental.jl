Extension: VK_KHR_video_queue

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `create_info::VideoSessionParametersCreateInfoKHR`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionParametersKHR.html)

```julia
create_video_session_parameters_khr(
    device,
    create_info::Vulkan.VideoSessionParametersCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.VideoSessionParametersKHR, Vulkan.VulkanError}

```
