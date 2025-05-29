Extension: VK_KHR_display

Arguments:

  * `min_src_position::_Offset2D`
  * `max_src_position::_Offset2D`
  * `min_src_extent::_Extent2D`
  * `max_src_extent::_Extent2D`
  * `min_dst_position::_Offset2D`
  * `max_dst_position::_Offset2D`
  * `min_dst_extent::_Extent2D`
  * `max_dst_extent::_Extent2D`
  * `supported_alpha::DisplayPlaneAlphaFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneCapabilitiesKHR.html)

```julia
_DisplayPlaneCapabilitiesKHR(
    min_src_position::Vulkan._Offset2D,
    max_src_position::Vulkan._Offset2D,
    min_src_extent::Vulkan._Extent2D,
    max_src_extent::Vulkan._Extent2D,
    min_dst_position::Vulkan._Offset2D,
    max_dst_position::Vulkan._Offset2D,
    min_dst_extent::Vulkan._Extent2D,
    max_dst_extent::Vulkan._Extent2D;
    supported_alpha
) -> Vulkan._DisplayPlaneCapabilitiesKHR

```
