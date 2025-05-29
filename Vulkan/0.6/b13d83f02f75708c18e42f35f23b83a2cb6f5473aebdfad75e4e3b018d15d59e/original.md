Extension: VK_KHR_video_queue

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `device::Device`
  * `video_session::VideoSessionKHR`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `video_session_parameters_template::VideoSessionParametersKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionParametersKHR.html)

```julia
_create_video_session_parameters_khr(
    device,
    video_session;
    allocator,
    next,
    flags,
    video_session_parameters_template
) -> ResultTypes.Result{Vulkan.VideoSessionParametersKHR, Vulkan.VulkanError}

```
