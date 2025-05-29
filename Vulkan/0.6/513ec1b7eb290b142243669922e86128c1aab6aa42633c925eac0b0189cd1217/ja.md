拡張: VK*KHR*video_queue

引数:

  * `device::Device`
  * `video_session::VideoSessionKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `video_session_parameters_template::VideoSessionParametersKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionParametersKHR.html)

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
