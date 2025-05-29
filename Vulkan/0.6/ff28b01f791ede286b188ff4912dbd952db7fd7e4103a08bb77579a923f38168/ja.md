拡張: VK*KHR*video_queue

引数:

  * `video_session::VideoSessionKHR`
  * `reference_slots::Vector{VideoReferenceSlotInfoKHR}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `video_session_parameters::VideoSessionParametersKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoBeginCodingInfoKHR.html)

```julia
VideoBeginCodingInfoKHR(
    video_session::Vulkan.VideoSessionKHR,
    reference_slots::AbstractArray;
    next,
    flags,
    video_session_parameters
) -> Vulkan.VideoBeginCodingInfoKHR

```
