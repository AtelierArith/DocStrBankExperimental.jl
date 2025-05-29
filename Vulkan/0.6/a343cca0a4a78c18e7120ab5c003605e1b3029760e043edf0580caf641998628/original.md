Extension: VK_KHR_video_decode_queue

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `video_usage_hints::VideoDecodeUsageFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeUsageInfoKHR.html)

```julia
_VideoDecodeUsageInfoKHR(
;
    next,
    video_usage_hints
) -> Vulkan._VideoDecodeUsageInfoKHR

```
