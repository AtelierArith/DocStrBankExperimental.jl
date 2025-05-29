拡張: VK*KHR*video*decode*queue

引数:

  * `src_buffer::Buffer`
  * `src_buffer_offset::UInt64`
  * `src_buffer_range::UInt64`
  * `dst_picture_resource::VideoPictureResourceInfoKHR`
  * `setup_reference_slot::VideoReferenceSlotInfoKHR`
  * `reference_slots::Vector{VideoReferenceSlotInfoKHR}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeInfoKHR.html)

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
