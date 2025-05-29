Extension: VK_KHR_video_decode_queue

Arguments:

  * `src_buffer::Buffer`
  * `src_buffer_offset::UInt64`
  * `src_buffer_range::UInt64`
  * `dst_picture_resource::_VideoPictureResourceInfoKHR`
  * `setup_reference_slot::_VideoReferenceSlotInfoKHR`
  * `reference_slots::Vector{_VideoReferenceSlotInfoKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeInfoKHR.html)

```julia
_VideoDecodeInfoKHR(
    src_buffer,
    src_buffer_offset::Integer,
    src_buffer_range::Integer,
    dst_picture_resource::Vulkan._VideoPictureResourceInfoKHR,
    setup_reference_slot::Vulkan._VideoReferenceSlotInfoKHR,
    reference_slots::AbstractArray;
    next,
    flags
) -> Vulkan._VideoDecodeInfoKHR

```
