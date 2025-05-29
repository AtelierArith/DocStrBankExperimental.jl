拡張: VK*QCOM*image_processing

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `max_weight_filter_phases::UInt32`: デフォルトは `0`
  * `max_weight_filter_dimension::_Extent2D`: デフォルトは `0`
  * `max_block_match_region::_Extent2D`: デフォルトは `0`
  * `max_box_filter_block_size::_Extent2D`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageProcessingPropertiesQCOM.html)

```julia
_PhysicalDeviceImageProcessingPropertiesQCOM(
;
    next,
    max_weight_filter_phases,
    max_weight_filter_dimension,
    max_block_match_region,
    max_box_filter_block_size
)

```
