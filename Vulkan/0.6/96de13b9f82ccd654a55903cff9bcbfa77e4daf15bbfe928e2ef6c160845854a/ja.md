引数:

  * `filter_minmax_single_component_formats::Bool`
  * `filter_minmax_image_component_mapping::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSamplerFilterMinmaxProperties.html)

```julia
_PhysicalDeviceSamplerFilterMinmaxProperties(
    filter_minmax_single_component_formats::Bool,
    filter_minmax_image_component_mapping::Bool;
    next
) -> Vulkan._PhysicalDeviceSamplerFilterMinmaxProperties

```
