拡張: VK*KHR*display

引数:

  * `min_src_position::Offset2D`
  * `max_src_position::Offset2D`
  * `min_src_extent::Extent2D`
  * `max_src_extent::Extent2D`
  * `min_dst_position::Offset2D`
  * `max_dst_position::Offset2D`
  * `min_dst_extent::Extent2D`
  * `max_dst_extent::Extent2D`
  * `supported_alpha::DisplayPlaneAlphaFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneCapabilitiesKHR.html)

```julia
DisplayPlaneCapabilitiesKHR(
    min_src_position::Vulkan.Offset2D,
    max_src_position::Vulkan.Offset2D,
    min_src_extent::Vulkan.Extent2D,
    max_src_extent::Vulkan.Extent2D,
    min_dst_position::Vulkan.Offset2D,
    max_dst_position::Vulkan.Offset2D,
    min_dst_extent::Vulkan.Extent2D,
    max_dst_extent::Vulkan.Extent2D;
    supported_alpha
) -> Vulkan.DisplayPlaneCapabilitiesKHR

```
