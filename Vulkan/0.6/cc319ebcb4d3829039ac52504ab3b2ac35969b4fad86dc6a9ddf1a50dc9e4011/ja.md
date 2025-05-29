拡張: VK*EXT*conservative_rasterization

引数:

  * `primitive_overestimation_size::Float32`
  * `max_extra_primitive_overestimation_size::Float32`
  * `extra_primitive_overestimation_size_granularity::Float32`
  * `primitive_underestimation::Bool`
  * `conservative_point_and_line_rasterization::Bool`
  * `degenerate_triangles_rasterized::Bool`
  * `degenerate_lines_rasterized::Bool`
  * `fully_covered_fragment_shader_input_variable::Bool`
  * `conservative_rasterization_post_depth_coverage::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceConservativeRasterizationPropertiesEXT.html)

```julia
PhysicalDeviceConservativeRasterizationPropertiesEXT(
    primitive_overestimation_size::Real,
    max_extra_primitive_overestimation_size::Real,
    extra_primitive_overestimation_size_granularity::Real,
    primitive_underestimation::Bool,
    conservative_point_and_line_rasterization::Bool,
    degenerate_triangles_rasterized::Bool,
    degenerate_lines_rasterized::Bool,
    fully_covered_fragment_shader_input_variable::Bool,
    conservative_rasterization_post_depth_coverage::Bool;
    next
) -> Vulkan.PhysicalDeviceConservativeRasterizationPropertiesEXT

```
