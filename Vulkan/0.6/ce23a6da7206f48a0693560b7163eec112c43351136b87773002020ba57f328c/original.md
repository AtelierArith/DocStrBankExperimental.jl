High-level wrapper for VkDisplayPlaneCapabilitiesKHR.

Extension: VK_KHR_display

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneCapabilitiesKHR.html)

```julia
struct DisplayPlaneCapabilitiesKHR <: Vulkan.HighLevelStruct
```

  * `supported_alpha::Vulkan.DisplayPlaneAlphaFlagKHR`
  * `min_src_position::Vulkan.Offset2D`
  * `max_src_position::Vulkan.Offset2D`
  * `min_src_extent::Vulkan.Extent2D`
  * `max_src_extent::Vulkan.Extent2D`
  * `min_dst_position::Vulkan.Offset2D`
  * `max_dst_position::Vulkan.Offset2D`
  * `min_dst_extent::Vulkan.Extent2D`
  * `max_dst_extent::Vulkan.Extent2D`
