Extension: VK_EXT_fragment_density_map2

Arguments:

  * `subsampled_loads::Bool`
  * `subsampled_coarse_reconstruction_early_access::Bool`
  * `max_subsampled_array_layers::UInt32`
  * `max_descriptor_set_subsampled_samplers::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFragmentDensityMap2PropertiesEXT.html)

```julia
PhysicalDeviceFragmentDensityMap2PropertiesEXT(
    subsampled_loads::Bool,
    subsampled_coarse_reconstruction_early_access::Bool,
    max_subsampled_array_layers::Integer,
    max_descriptor_set_subsampled_samplers::Integer;
    next
) -> Vulkan.PhysicalDeviceFragmentDensityMap2PropertiesEXT

```
