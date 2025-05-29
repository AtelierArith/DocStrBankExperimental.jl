VkVideoDecodeInfoKHRの高レベルラッパー。

拡張: VK*KHR*video*decode*queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeInfoKHR.html)

```julia
struct VideoDecodeInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `src_buffer::Vulkan.Buffer`
  * `src_buffer_offset::UInt64`
  * `src_buffer_range::UInt64`
  * `dst_picture_resource::Vulkan.VideoPictureResourceInfoKHR`
  * `setup_reference_slot::Union{Ptr{Nothing}, Vulkan.VideoReferenceSlotInfoKHR}`
  * `reference_slots::Vector{Vulkan.VideoReferenceSlotInfoKHR}`
