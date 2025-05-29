Extension: VK_KHR_video_decode_queue

Arguments:

  * `src_buffer::Buffer`
  * `src_buffer_offset::UInt64`
  * `src_buffer_range::UInt64`
  * `dst_picture_resource::VideoPictureResourceInfoKHR`
  * `setup_reference_slot::VideoReferenceSlotInfoKHR`
  * `reference_slots::Vector{VideoReferenceSlotInfoKHR}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeInfoKHR.html)

```julia
VideoDecodeInfoKHR(
    src_buffer::Vulkan.Buffer,
    src_buffer_offset::Integer,
    src_buffer_range::Integer,
    dst_picture_resource::Vulkan.VideoPictureResourceInfoKHR,
    setup_reference_slot::Vulkan.VideoReferenceSlotInfoKHR,
    reference_slots::AbstractArray;
    next,
    flags
) -> Vulkan.VideoDecodeInfoKHR

```
