拡張: VK*QCOM*image_processing

引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `max_weight_filter_phases::UInt32`: デフォルトは `0`
  * `max_weight_filter_dimension::Extent2D`: デフォルトは `C_NULL`
  * `max_block_match_region::Extent2D`: デフォルトは `C_NULL`
  * `max_box_filter_block_size::Extent2D`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageProcessingPropertiesQCOM.html)

```julia
PhysicalDeviceImageProcessingPropertiesQCOM(
;
    next,
    max_weight_filter_phases,
    max_weight_filter_dimension,
    max_block_match_region,
    max_box_filter_block_size
) -> Vulkan.PhysicalDeviceImageProcessingPropertiesQCOM

```
