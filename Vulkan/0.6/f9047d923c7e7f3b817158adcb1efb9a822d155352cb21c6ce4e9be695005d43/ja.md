拡張機能: VK*KHR*video_queue

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_VIDEO_STD_VERSION_NOT_SUPPORTED_KHR`

引数:

  * `device::Device`
  * `create_info::VideoSessionCreateInfoKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionKHR.html)

```julia
create_video_session_khr(
    device,
    create_info::Vulkan.VideoSessionCreateInfoKHR;
    allocator
)

```
