VkVideoReferenceSlotInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoReferenceSlotInfoKHR.html)

```julia
struct VideoReferenceSlotInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `slot_index::Int32`
  * `picture_resource::Union{Ptr{Nothing}, Vulkan.VideoPictureResourceInfoKHR}`
