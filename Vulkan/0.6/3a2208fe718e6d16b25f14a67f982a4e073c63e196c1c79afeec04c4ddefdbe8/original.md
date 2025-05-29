Extension: VK_KHR_video_decode_h264

Arguments:

  * `max_level_idc::StdVideoH264LevelIdc`
  * `field_offset_granularity::_Offset2D`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH264CapabilitiesKHR.html)

```julia
_VideoDecodeH264CapabilitiesKHR(
    max_level_idc::VulkanCore.LibVulkan.StdVideoH264LevelIdc,
    field_offset_granularity::Vulkan._Offset2D;
    next
) -> Vulkan._VideoDecodeH264CapabilitiesKHR

```
