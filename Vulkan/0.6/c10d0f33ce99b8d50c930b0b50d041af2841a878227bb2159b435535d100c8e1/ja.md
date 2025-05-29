拡張: VK*KHR*video*decode*h265

引数:

  * `max_level_idc::StdVideoH265LevelIdc`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeH265CapabilitiesKHR.html)

```julia
_VideoDecodeH265CapabilitiesKHR(
    max_level_idc::VulkanCore.LibVulkan.StdVideoH265LevelIdc;
    next
) -> Vulkan._VideoDecodeH265CapabilitiesKHR

```
