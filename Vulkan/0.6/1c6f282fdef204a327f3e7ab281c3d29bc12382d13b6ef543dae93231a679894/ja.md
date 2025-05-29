拡張: VK*KHR*video_queue

引数:

  * `video_codec_operations::VideoCodecOperationFlagKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyVideoPropertiesKHR.html)

```julia
_QueueFamilyVideoPropertiesKHR(
    video_codec_operations::Vulkan.VideoCodecOperationFlagKHR;
    next
) -> Vulkan._QueueFamilyVideoPropertiesKHR

```
