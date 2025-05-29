Extension: VK_KHR_video_queue

Arguments:

  * `video_codec_operation::VideoCodecOperationFlagKHR`
  * `chroma_subsampling::VideoChromaSubsamplingFlagKHR`
  * `luma_bit_depth::VideoComponentBitDepthFlagKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `chroma_bit_depth::VideoComponentBitDepthFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileInfoKHR.html)

```julia
_VideoProfileInfoKHR(
    video_codec_operation::Vulkan.VideoCodecOperationFlagKHR,
    chroma_subsampling::Vulkan.VideoChromaSubsamplingFlagKHR,
    luma_bit_depth::Vulkan.VideoComponentBitDepthFlagKHR;
    next,
    chroma_bit_depth
) -> Vulkan._VideoProfileInfoKHR

```
