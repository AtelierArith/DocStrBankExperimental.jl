Extension: VK_EXT_fragment_density_map

Arguments:

  * `min_fragment_density_texel_size::_Extent2D`
  * `max_fragment_density_texel_size::_Extent2D`
  * `fragment_density_invocations::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMapPropertiesEXT.html)

```julia
_PhysicalDeviceFragmentDensityMapPropertiesEXT(
    min_fragment_density_texel_size::Vulkan._Extent2D,
    max_fragment_density_texel_size::Vulkan._Extent2D,
    fragment_density_invocations::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentDensityMapPropertiesEXT

```
