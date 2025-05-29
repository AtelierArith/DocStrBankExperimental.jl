Extension: VK_QCOM_image_processing

Arguments:

  * `next::Any`: defaults to `C_NULL`
  * `max_weight_filter_phases::UInt32`: defaults to `0`
  * `max_weight_filter_dimension::Extent2D`: defaults to `C_NULL`
  * `max_block_match_region::Extent2D`: defaults to `C_NULL`
  * `max_box_filter_block_size::Extent2D`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageProcessingPropertiesQCOM.html)

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
