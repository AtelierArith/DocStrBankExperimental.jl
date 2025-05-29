拡張: VK*EXT*fragment*density*map

引数:

  * `min_fragment_density_texel_size::_Extent2D`
  * `max_fragment_density_texel_size::_Extent2D`
  * `fragment_density_invocations::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMapPropertiesEXT.html)

```julia
_PhysicalDeviceFragmentDensityMapPropertiesEXT(
    min_fragment_density_texel_size::Vulkan._Extent2D,
    max_fragment_density_texel_size::Vulkan._Extent2D,
    fragment_density_invocations::Bool;
    next
) -> Vulkan._PhysicalDeviceFragmentDensityMapPropertiesEXT

```
