拡張: VK*EXT*sample_locations

引数:

  * `sample_locations_per_pixel::SampleCountFlag`
  * `sample_location_grid_size::Extent2D`
  * `sample_locations::Vector{SampleLocationEXT}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSampleLocationsInfoEXT.html)

```julia
SampleLocationsInfoEXT(
    sample_locations_per_pixel::Vulkan.SampleCountFlag,
    sample_location_grid_size::Vulkan.Extent2D,
    sample_locations::AbstractArray;
    next
) -> Vulkan.SampleLocationsInfoEXT

```
