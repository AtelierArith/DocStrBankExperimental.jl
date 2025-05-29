引数:

  * `depth_clamp_enable::Bool`
  * `rasterizer_discard_enable::Bool`
  * `polygon_mode::PolygonMode`
  * `front_face::FrontFace`
  * `depth_bias_enable::Bool`
  * `depth_bias_constant_factor::Float32`
  * `depth_bias_clamp::Float32`
  * `depth_bias_slope_factor::Float32`
  * `line_width::Float32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `cull_mode::CullModeFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationStateCreateInfo.html)

```julia
_PipelineRasterizationStateCreateInfo(
    depth_clamp_enable::Bool,
    rasterizer_discard_enable::Bool,
    polygon_mode::Vulkan.PolygonMode,
    front_face::Vulkan.FrontFace,
    depth_bias_enable::Bool,
    depth_bias_constant_factor::Real,
    depth_bias_clamp::Real,
    depth_bias_slope_factor::Real,
    line_width::Real;
    next,
    flags,
    cull_mode
) -> Vulkan._PipelineRasterizationStateCreateInfo

```
