Extension: VK_QCOM_image_processing

Arguments:

  * `filter_center::Offset2D`
  * `filter_size::Extent2D`
  * `num_phases::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewSampleWeightCreateInfoQCOM.html)

```julia
ImageViewSampleWeightCreateInfoQCOM(
    filter_center::Vulkan.Offset2D,
    filter_size::Vulkan.Extent2D,
    num_phases::Integer;
    next
) -> Vulkan.ImageViewSampleWeightCreateInfoQCOM

```
