Extension: VK_KHR_video_decode_h264

Arguments:

  * `max_level_idc::StdVideoH264LevelIdc`
  * `field_offset_granularity::Offset2D`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264CapabilitiesKHR.html)

```julia
VideoDecodeH264CapabilitiesKHR(
    max_level_idc::VulkanCore.LibVulkan.StdVideoH264LevelIdc,
    field_offset_granularity::Vulkan.Offset2D;
    next
) -> Vulkan.VideoDecodeH264CapabilitiesKHR

```
