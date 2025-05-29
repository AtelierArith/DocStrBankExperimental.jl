拡張: VK*EXT*line_rasterization

引数:

  * `rectangular_lines::Bool`
  * `bresenham_lines::Bool`
  * `smooth_lines::Bool`
  * `stippled_rectangular_lines::Bool`
  * `stippled_bresenham_lines::Bool`
  * `stippled_smooth_lines::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceLineRasterizationFeaturesEXT.html)

```julia
PhysicalDeviceLineRasterizationFeaturesEXT(
    rectangular_lines::Bool,
    bresenham_lines::Bool,
    smooth_lines::Bool,
    stippled_rectangular_lines::Bool,
    stippled_bresenham_lines::Bool,
    stippled_smooth_lines::Bool;
    next
) -> Vulkan.PhysicalDeviceLineRasterizationFeaturesEXT

```
