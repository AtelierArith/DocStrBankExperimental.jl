High-level wrapper for VkVideoBeginCodingInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoBeginCodingInfoKHR.html)

```julia
struct VideoBeginCodingInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `video_session::Vulkan.VideoSessionKHR`
  * `video_session_parameters::Union{Ptr{Nothing}, Vulkan.VideoSessionParametersKHR}`
  * `reference_slots::Vector{Vulkan.VideoReferenceSlotInfoKHR}`
