拡張: VK*EXT*fragment*density*map2

引数:

  * `subsampled_loads::Bool`
  * `subsampled_coarse_reconstruction_early_access::Bool`
  * `max_subsampled_array_layers::UInt32`
  * `max_descriptor_set_subsampled_samplers::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMap2PropertiesEXT.html)

```julia
_PhysicalDeviceFragmentDensityMap2PropertiesEXT(
    subsampled_loads::Bool,
    subsampled_coarse_reconstruction_early_access::Bool,
    max_subsampled_array_layers::Integer,
    max_descriptor_set_subsampled_samplers::Integer;
    next
) -> Vulkan._PhysicalDeviceFragmentDensityMap2PropertiesEXT

```
