High-level wrapper for VkImageViewSampleWeightCreateInfoQCOM.

Extension: VK_QCOM_image_processing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewSampleWeightCreateInfoQCOM.html)

```julia
struct ImageViewSampleWeightCreateInfoQCOM <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `filter_center::Vulkan.Offset2D`
  * `filter_size::Vulkan.Extent2D`
  * `num_phases::UInt32`
