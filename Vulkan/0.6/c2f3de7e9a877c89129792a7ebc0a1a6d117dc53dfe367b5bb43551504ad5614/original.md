Extension: VK_KHR_video_queue

Arguments:

  * `device::Device`
  * `video_session::VideoSessionKHR` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyVideoSessionKHR.html)

```julia
destroy_video_session_khr(device, video_session; allocator)

```
