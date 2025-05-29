拡張: VK*EXT*fragment*density*map

引数:

  * `fragment_density_map::Bool`
  * `fragment_density_map_dynamic::Bool`
  * `fragment_density_map_non_subsampled_images::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMapFeaturesEXT.html)

```julia
_PhysicalDeviceFragmentDensityMapFeaturesEXT(
    fragment_density_map::Bool,
    fragment_density_map_dynamic::Bool,
    fragment_density_map_non_subsampled_images::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentDensityMapFeaturesEXT

```
