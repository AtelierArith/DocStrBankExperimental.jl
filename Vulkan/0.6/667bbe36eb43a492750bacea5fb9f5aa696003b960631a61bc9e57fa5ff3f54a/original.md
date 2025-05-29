High-level wrapper for VkVideoReferenceSlotInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoReferenceSlotInfoKHR.html)

```julia
struct VideoReferenceSlotInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `slot_index::Int32`
  * `picture_resource::Union{Ptr{Nothing}, Vulkan.VideoPictureResourceInfoKHR}`
