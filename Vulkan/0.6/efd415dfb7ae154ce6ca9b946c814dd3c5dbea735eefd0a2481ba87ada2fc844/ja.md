VkVideoProfileInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileInfoKHR.html)

```julia
struct VideoProfileInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `video_codec_operation::Vulkan.VideoCodecOperationFlagKHR`
  * `chroma_subsampling::Vulkan.VideoChromaSubsamplingFlagKHR`
  * `luma_bit_depth::Vulkan.VideoComponentBitDepthFlagKHR`
  * `chroma_bit_depth::Vulkan.VideoComponentBitDepthFlagKHR`
