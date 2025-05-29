Extension: VK_KHR_video_queue

Arguments:

  * `device::Device`
  * `video_session::VideoSessionKHR`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `video_session_parameters_template::VideoSessionParametersKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionParametersKHR.html)

```julia
VideoSessionParametersKHR(
    device,
    video_session;
    allocator,
    next,
    flags,
    video_session_parameters_template
) -> Vulkan.VideoSessionParametersKHR

```
