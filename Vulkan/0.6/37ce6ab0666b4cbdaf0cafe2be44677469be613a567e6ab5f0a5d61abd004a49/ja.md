拡張: VK*NV*ray_tracing

引数:

  * `stages::Vector{PipelineShaderStageCreateInfo}`
  * `groups::Vector{RayTracingShaderGroupCreateInfoNV}`
  * `max_recursion_depth::UInt32`
  * `layout::PipelineLayout`
  * `base_pipeline_index::Int32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::PipelineCreateFlag`: デフォルトは `0`
  * `base_pipeline_handle::Pipeline`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineCreateInfoNV.html)

```julia
RayTracingPipelineCreateInfoNV(
    stages::AbstractArray,
    groups::AbstractArray,
    max_recursion_depth::Integer,
    layout::Vulkan.PipelineLayout,
    base_pipeline_index::Integer;
    next,
    flags,
    base_pipeline_handle
) -> Vulkan.RayTracingPipelineCreateInfoNV

```
