Extension: VK_KHR_video_queue

Arguments:

  * `video_session::VideoSessionKHR`
  * `reference_slots::Vector{_VideoReferenceSlotInfoKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `video_session_parameters::VideoSessionParametersKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoBeginCodingInfoKHR.html)

```julia
_VideoBeginCodingInfoKHR(
    video_session,
    reference_slots::AbstractArray;
    next,
    flags,
    video_session_parameters
) -> Vulkan._VideoBeginCodingInfoKHR

```
