拡張機能: VK*KHR*video_queue

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `device::Device`
  * `video_session::VideoSessionKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `video_session_parameters_template::VideoSessionParametersKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionParametersKHR.html)

```julia
create_video_session_parameters_khr(
    device,
    video_session;
    allocator,
    next,
    flags,
    video_session_parameters_template
) -> ResultTypes.Result{Vulkan.VideoSessionParametersKHR, Vulkan.VulkanError}

```
