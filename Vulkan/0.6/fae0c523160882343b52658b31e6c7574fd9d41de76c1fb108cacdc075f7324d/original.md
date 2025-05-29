Extension: VK_EXT_sample_locations

Arguments:

  * `sample_locations_per_pixel::SampleCountFlag`
  * `sample_location_grid_size::_Extent2D`
  * `sample_locations::Vector{_SampleLocationEXT}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSampleLocationsInfoEXT.html)

```julia
_SampleLocationsInfoEXT(
    sample_locations_per_pixel::Vulkan.SampleCountFlag,
    sample_location_grid_size::Vulkan._Extent2D,
    sample_locations::AbstractArray;
    next
) -> Vulkan._SampleLocationsInfoEXT

```
