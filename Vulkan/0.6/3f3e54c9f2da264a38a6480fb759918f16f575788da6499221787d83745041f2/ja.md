拡張: VK*QCOM*image_processing

引数:

  * `texture_sample_weighted::Bool`
  * `texture_box_filter::Bool`
  * `texture_block_match::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageProcessingFeaturesQCOM.html)

```julia
_PhysicalDeviceImageProcessingFeaturesQCOM(
    texture_sample_weighted::Bool,
    texture_box_filter::Bool,
    texture_block_match::Bool;
    next
) -> Vulkan._PhysicalDeviceImageProcessingFeaturesQCOM

```
