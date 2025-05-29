Extension: VK_KHR_video_queue

Arguments:

  * `device::Device`
  * `video_session_parameters::VideoSessionParametersKHR` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyVideoSessionParametersKHR.html)

```julia
_destroy_video_session_parameters_khr(
    device,
    video_session_parameters;
    allocator
)

```
