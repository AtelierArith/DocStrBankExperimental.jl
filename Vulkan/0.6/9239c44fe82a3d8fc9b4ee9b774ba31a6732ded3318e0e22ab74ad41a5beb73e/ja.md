拡張機能: VK*KHR*video_queue

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `video_session::VideoSessionKHR` (externsync)
  * `bind_session_memory_infos::Vector{_BindVideoSessionMemoryInfoKHR}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBindVideoSessionMemoryKHR.html)

```julia
_bind_video_session_memory_khr(
    device,
    video_session,
    bind_session_memory_infos::AbstractArray
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
