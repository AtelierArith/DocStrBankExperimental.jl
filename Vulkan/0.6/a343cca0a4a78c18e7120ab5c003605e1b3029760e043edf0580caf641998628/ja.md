拡張: VK*KHR*video*decode*queue

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `video_usage_hints::VideoDecodeUsageFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeUsageInfoKHR.html)

```julia
_VideoDecodeUsageInfoKHR(
;
    next,
    video_usage_hints
) -> Vulkan._VideoDecodeUsageInfoKHR

```
