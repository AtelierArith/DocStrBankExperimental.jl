拡張: VK*EXT*line_rasterization

引数:

  * `line_rasterization_mode::LineRasterizationModeEXT`
  * `stippled_line_enable::Bool`
  * `line_stipple_factor::UInt32`
  * `line_stipple_pattern::UInt16`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationLineStateCreateInfoEXT.html)

```julia
PipelineRasterizationLineStateCreateInfoEXT(
    line_rasterization_mode::Vulkan.LineRasterizationModeEXT,
    stippled_line_enable::Bool,
    line_stipple_factor::Integer,
    line_stipple_pattern::Integer;
    next
) -> Vulkan.PipelineRasterizationLineStateCreateInfoEXT

```
