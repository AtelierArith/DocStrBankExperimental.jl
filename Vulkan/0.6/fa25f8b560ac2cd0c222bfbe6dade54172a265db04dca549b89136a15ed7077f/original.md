Extension: VK_EXT_sample_locations

Arguments:

  * `sample_location_sample_counts::SampleCountFlag`
  * `max_sample_location_grid_size::Extent2D`
  * `sample_location_coordinate_range::NTuple{2, Float32}`
  * `sample_location_sub_pixel_bits::UInt32`
  * `variable_sample_locations::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSampleLocationsPropertiesEXT.html)

```julia
PhysicalDeviceSampleLocationsPropertiesEXT(
    sample_location_sample_counts::Vulkan.SampleCountFlag,
    max_sample_location_grid_size::Vulkan.Extent2D,
    sample_location_coordinate_range::Tuple{Float32, Float32},
    sample_location_sub_pixel_bits::Integer,
    variable_sample_locations::Bool;
    next
) -> Vulkan.PhysicalDeviceSampleLocationsPropertiesEXT

```
