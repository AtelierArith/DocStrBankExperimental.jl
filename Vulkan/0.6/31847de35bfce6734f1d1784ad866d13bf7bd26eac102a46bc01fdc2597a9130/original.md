Extension: VK_EXT_fragment_density_map

Arguments:

  * `fragment_density_map::Bool`
  * `fragment_density_map_dynamic::Bool`
  * `fragment_density_map_non_subsampled_images::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMapFeaturesEXT.html)

```julia
_PhysicalDeviceFragmentDensityMapFeaturesEXT(
    fragment_density_map::Bool,
    fragment_density_map_dynamic::Bool,
    fragment_density_map_non_subsampled_images::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentDensityMapFeaturesEXT

```
