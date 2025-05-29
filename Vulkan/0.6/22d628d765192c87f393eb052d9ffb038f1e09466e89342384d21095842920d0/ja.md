VkPhysicalDeviceLineRasterizationFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*line_rasterization

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceLineRasterizationFeaturesEXT.html)

```julia
struct PhysicalDeviceLineRasterizationFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `rectangular_lines::Bool`
  * `bresenham_lines::Bool`
  * `smooth_lines::Bool`
  * `stippled_rectangular_lines::Bool`
  * `stippled_bresenham_lines::Bool`
  * `stippled_smooth_lines::Bool`
