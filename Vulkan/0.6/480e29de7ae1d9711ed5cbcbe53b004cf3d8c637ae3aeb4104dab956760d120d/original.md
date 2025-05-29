Extension: VK_KHR_video_queue

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `video_session::VideoSessionKHR` (externsync)
  * `bind_session_memory_infos::Vector{BindVideoSessionMemoryInfoKHR}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindVideoSessionMemoryKHR.html)

```julia
bind_video_session_memory_khr(
    device,
    video_session,
    bind_session_memory_infos::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
