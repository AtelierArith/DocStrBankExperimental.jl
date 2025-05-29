拡張: VK*EXT*fragment*density*map

引数:

  * `min_fragment_density_texel_size::Extent2D`
  * `max_fragment_density_texel_size::Extent2D`
  * `fragment_density_invocations::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMapPropertiesEXT.html)

```julia
PhysicalDeviceFragmentDensityMapPropertiesEXT(
    min_fragment_density_texel_size::Vulkan.Extent2D,
    max_fragment_density_texel_size::Vulkan.Extent2D,
    fragment_density_invocations::Bool;
    next
) -> Vulkan.PhysicalDeviceFragmentDensityMapPropertiesEXT

```
