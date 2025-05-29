Extension: VK_KHR_video_decode_h265

Arguments:

  * `max_level_idc::StdVideoH265LevelIdc`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265CapabilitiesKHR.html)

```julia
_VideoDecodeH265CapabilitiesKHR(
    max_level_idc::VulkanCore.LibVulkan.StdVideoH265LevelIdc;
    next
) -> Vulkan._VideoDecodeH265CapabilitiesKHR

```
