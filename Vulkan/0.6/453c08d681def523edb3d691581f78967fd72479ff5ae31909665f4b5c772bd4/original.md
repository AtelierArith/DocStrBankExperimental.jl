Extension: VK_QCOM_image_processing

Arguments:

  * `texture_sample_weighted::Bool`
  * `texture_box_filter::Bool`
  * `texture_block_match::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageProcessingFeaturesQCOM.html)

```julia
PhysicalDeviceImageProcessingFeaturesQCOM(
    texture_sample_weighted::Bool,
    texture_box_filter::Bool,
    texture_block_match::Bool;
    next
) -> Vulkan.PhysicalDeviceImageProcessingFeaturesQCOM

```
