High-level wrapper for VkPipelineRasterizationStateCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRasterizationStateCreateInfo.html)

```julia
struct PipelineRasterizationStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `depth_clamp_enable::Bool`
  * `rasterizer_discard_enable::Bool`
  * `polygon_mode::Vulkan.PolygonMode`
  * `cull_mode::Vulkan.CullModeFlag`
  * `front_face::Vulkan.FrontFace`
  * `depth_bias_enable::Bool`
  * `depth_bias_constant_factor::Float32`
  * `depth_bias_clamp::Float32`
  * `depth_bias_slope_factor::Float32`
  * `line_width::Float32`
