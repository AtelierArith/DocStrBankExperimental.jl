VkVideoBeginCodingInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoBeginCodingInfoKHR.html)

```julia
struct VideoBeginCodingInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `video_session::Vulkan.VideoSessionKHR`
  * `video_session_parameters::Union{Ptr{Nothing}, Vulkan.VideoSessionParametersKHR}`
  * `reference_slots::Vector{Vulkan.VideoReferenceSlotInfoKHR}`
