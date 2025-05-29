Extension: VK_KHR_video_queue

Arguments:

  * `slot_index::Int32`
  * `next::Any`: defaults to `C_NULL`
  * `picture_resource::VideoPictureResourceInfoKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoReferenceSlotInfoKHR.html)

```julia
VideoReferenceSlotInfoKHR(
    slot_index::Integer;
    next,
    picture_resource
) -> Vulkan.VideoReferenceSlotInfoKHR

```
