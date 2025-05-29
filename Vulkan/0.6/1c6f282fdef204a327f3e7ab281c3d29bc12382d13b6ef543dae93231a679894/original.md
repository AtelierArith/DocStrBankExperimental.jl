Extension: VK_KHR_video_queue

Arguments:

  * `video_codec_operations::VideoCodecOperationFlagKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyVideoPropertiesKHR.html)

```julia
_QueueFamilyVideoPropertiesKHR(
    video_codec_operations::Vulkan.VideoCodecOperationFlagKHR;
    next
) -> Vulkan._QueueFamilyVideoPropertiesKHR

```
