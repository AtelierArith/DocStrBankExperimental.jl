Extension: VK_KHR_video_queue

Arguments:

  * `device::Device`
  * `video_session::VideoSessionKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetVideoSessionMemoryRequirementsKHR.html)

```julia
get_video_session_memory_requirements_khr(
    device,
    video_session
) -> Vector{Vulkan.VideoSessionMemoryRequirementsKHR}

```
