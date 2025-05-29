拡張: VK*KHR*video*decode*h264

引数:

  * `max_level_idc::StdVideoH264LevelIdc`
  * `field_offset_granularity::Offset2D`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264CapabilitiesKHR.html)

```julia
VideoDecodeH264CapabilitiesKHR(
    max_level_idc::VulkanCore.LibVulkan.StdVideoH264LevelIdc,
    field_offset_granularity::Vulkan.Offset2D;
    next
) -> Vulkan.VideoDecodeH264CapabilitiesKHR

```
