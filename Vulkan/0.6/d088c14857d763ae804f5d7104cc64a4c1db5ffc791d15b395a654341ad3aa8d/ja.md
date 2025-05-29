High-level wrapper for VkPipelineRasterizationLineStateCreateInfoEXT.

Extension: VK*EXT*line_rasterization

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationLineStateCreateInfoEXT.html)

```julia
struct PipelineRasterizationLineStateCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `line_rasterization_mode::Vulkan.LineRasterizationModeEXT`
  * `stippled_line_enable::Bool`
  * `line_stipple_factor::UInt32`
  * `line_stipple_pattern::UInt16`
