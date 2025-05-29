Extension: VK_KHR_video_queue

Arguments:

  * `slot_index::Int32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `picture_resource::_VideoPictureResourceInfoKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoReferenceSlotInfoKHR.html)

```julia
_VideoReferenceSlotInfoKHR(
    slot_index::Integer;
    next,
    picture_resource
) -> Vulkan._VideoReferenceSlotInfoKHR

```
