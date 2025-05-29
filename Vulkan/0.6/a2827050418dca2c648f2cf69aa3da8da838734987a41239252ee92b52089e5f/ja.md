VkPhysicalDeviceSampleLocationsPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*sample_locations

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSampleLocationsPropertiesEXT.html)

```julia
struct PhysicalDeviceSampleLocationsPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `sample_location_sample_counts::Vulkan.SampleCountFlag`
  * `max_sample_location_grid_size::Vulkan.Extent2D`
  * `sample_location_coordinate_range::Tuple{Float32, Float32}`
  * `sample_location_sub_pixel_bits::UInt32`
  * `variable_sample_locations::Bool`
