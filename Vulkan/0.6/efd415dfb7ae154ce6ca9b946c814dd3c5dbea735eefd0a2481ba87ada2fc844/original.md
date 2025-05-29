High-level wrapper for VkVideoProfileInfoKHR.

Extension: VK_KHR_video_queue

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileInfoKHR.html)

```julia
struct VideoProfileInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `video_codec_operation::Vulkan.VideoCodecOperationFlagKHR`
  * `chroma_subsampling::Vulkan.VideoChromaSubsamplingFlagKHR`
  * `luma_bit_depth::Vulkan.VideoComponentBitDepthFlagKHR`
  * `chroma_bit_depth::Vulkan.VideoComponentBitDepthFlagKHR`
