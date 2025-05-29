拡張: VK*KHR*video_queue

引数:

  * `device::Device`
  * `video_session_parameters::VideoSessionParametersKHR` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyVideoSessionParametersKHR.html)

```julia
_destroy_video_session_parameters_khr(
    device,
    video_session_parameters;
    allocator
)

```
