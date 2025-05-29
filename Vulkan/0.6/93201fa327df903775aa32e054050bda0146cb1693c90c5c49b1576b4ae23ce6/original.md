Extension: VK_KHR_video_queue

Arguments:

  * `video_session::VideoSessionKHR`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `video_session_parameters_template::VideoSessionParametersKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionParametersCreateInfoKHR.html)

```julia
VideoSessionParametersCreateInfoKHR(
    video_session::Vulkan.VideoSessionKHR;
    next,
    flags,
    video_session_parameters_template
) -> Vulkan.VideoSessionParametersCreateInfoKHR

```
