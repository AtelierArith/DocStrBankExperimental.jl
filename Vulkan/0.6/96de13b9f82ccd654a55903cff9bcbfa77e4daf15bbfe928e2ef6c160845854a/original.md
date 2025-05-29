Arguments:

  * `filter_minmax_single_component_formats::Bool`
  * `filter_minmax_image_component_mapping::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSamplerFilterMinmaxProperties.html)

```julia
_PhysicalDeviceSamplerFilterMinmaxProperties(
    filter_minmax_single_component_formats::Bool,
    filter_minmax_image_component_mapping::Bool;
    next
) -> Vulkan._PhysicalDeviceSamplerFilterMinmaxProperties

```
