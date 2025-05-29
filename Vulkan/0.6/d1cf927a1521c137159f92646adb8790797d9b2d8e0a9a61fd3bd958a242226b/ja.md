VkSampleLocationsInfoEXTの高レベルラッパー。

拡張: VK*EXT*sample_locations

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSampleLocationsInfoEXT.html)

```julia
struct SampleLocationsInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `sample_locations_per_pixel::Vulkan.SampleCountFlag`
  * `sample_location_grid_size::Vulkan.Extent2D`
  * `sample_locations::Vector{Vulkan.SampleLocationEXT}`
