拡張: VK*KHR*video_queue

引数:

  * `slot_index::Int32`
  * `next::Any`: デフォルトは `C_NULL`
  * `picture_resource::VideoPictureResourceInfoKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoReferenceSlotInfoKHR.html)

```julia
VideoReferenceSlotInfoKHR(
    slot_index::Integer;
    next,
    picture_resource
) -> Vulkan.VideoReferenceSlotInfoKHR

```
