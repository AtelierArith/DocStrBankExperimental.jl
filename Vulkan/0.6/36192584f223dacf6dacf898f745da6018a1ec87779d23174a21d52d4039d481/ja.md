VkHdrMetadataEXTの高レベルラッパー。

拡張: VK*EXT*hdr_metadata

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkHdrMetadataEXT.html)

```julia
struct HdrMetadataEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `display_primary_red::Vulkan.XYColorEXT`
  * `display_primary_green::Vulkan.XYColorEXT`
  * `display_primary_blue::Vulkan.XYColorEXT`
  * `white_point::Vulkan.XYColorEXT`
  * `max_luminance::Float32`
  * `min_luminance::Float32`
  * `max_content_light_level::Float32`
  * `max_frame_average_light_level::Float32`
