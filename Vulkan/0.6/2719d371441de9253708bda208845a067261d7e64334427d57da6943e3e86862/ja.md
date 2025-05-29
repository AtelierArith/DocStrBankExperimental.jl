拡張: VK*KHR*video*decode*queue

引数:

  * `src_buffer::Buffer`
  * `src_buffer_offset::UInt64`
  * `src_buffer_range::UInt64`
  * `dst_picture_resource::_VideoPictureResourceInfoKHR`
  * `setup_reference_slot::_VideoReferenceSlotInfoKHR`
  * `reference_slots::Vector{_VideoReferenceSlotInfoKHR}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeInfoKHR.html)

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
