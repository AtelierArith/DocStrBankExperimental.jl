Extension: VK_NV_ray_tracing

Arguments:

  * `stages::Vector{_PipelineShaderStageCreateInfo}`
  * `groups::Vector{_RayTracingShaderGroupCreateInfoNV}`
  * `max_recursion_depth::UInt32`
  * `layout::PipelineLayout`
  * `base_pipeline_index::Int32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineCreateFlag`: defaults to `0`
  * `base_pipeline_handle::Pipeline`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineCreateInfoNV.html)

```julia
_RayTracingPipelineCreateInfoNV(
    stages::AbstractArray,
    groups::AbstractArray,
    max_recursion_depth::Integer,
    layout,
    base_pipeline_index::Integer;
    next,
    flags,
    base_pipeline_handle
) -> Vulkan._RayTracingPipelineCreateInfoNV

```
