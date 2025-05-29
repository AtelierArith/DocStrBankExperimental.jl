High-level wrapper for VkPhysicalDeviceImageProcessingPropertiesQCOM.

Extension: VK_QCOM_image_processing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageProcessingPropertiesQCOM.html)

```julia
struct PhysicalDeviceImageProcessingPropertiesQCOM <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_weight_filter_phases::UInt32`
  * `max_weight_filter_dimension::Union{Ptr{Nothing}, Vulkan.Extent2D}`
  * `max_block_match_region::Union{Ptr{Nothing}, Vulkan.Extent2D}`
  * `max_box_filter_block_size::Union{Ptr{Nothing}, Vulkan.Extent2D}`
