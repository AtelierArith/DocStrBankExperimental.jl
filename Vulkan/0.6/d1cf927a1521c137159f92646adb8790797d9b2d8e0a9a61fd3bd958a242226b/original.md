High-level wrapper for VkSampleLocationsInfoEXT.

Extension: VK_EXT_sample_locations

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSampleLocationsInfoEXT.html)

```julia
struct SampleLocationsInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `sample_locations_per_pixel::Vulkan.SampleCountFlag`
  * `sample_location_grid_size::Vulkan.Extent2D`
  * `sample_locations::Vector{Vulkan.SampleLocationEXT}`
