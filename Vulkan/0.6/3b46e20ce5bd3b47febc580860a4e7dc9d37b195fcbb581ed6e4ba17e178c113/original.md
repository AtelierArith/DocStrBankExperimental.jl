Extension: VK_QCOM_image_processing

Arguments:

  * `filter_center::_Offset2D`
  * `filter_size::_Extent2D`
  * `num_phases::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewSampleWeightCreateInfoQCOM.html)

```julia
_ImageViewSampleWeightCreateInfoQCOM(
    filter_center::Vulkan._Offset2D,
    filter_size::Vulkan._Extent2D,
    num_phases::Integer;
    next
) -> Vulkan._ImageViewSampleWeightCreateInfoQCOM

```
