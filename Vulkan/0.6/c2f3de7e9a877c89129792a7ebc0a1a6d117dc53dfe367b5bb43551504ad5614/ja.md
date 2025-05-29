拡張: VK*KHR*video_queue

引数:

  * `device::Device`
  * `video_session::VideoSessionKHR` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyVideoSessionKHR.html)

```julia
destroy_video_session_khr(device, video_session; allocator)

```
