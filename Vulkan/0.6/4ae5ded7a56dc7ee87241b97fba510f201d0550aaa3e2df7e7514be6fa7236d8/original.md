Extension: VK_KHR_ray_tracing_pipeline

Arguments:

  * `stages::Vector{PipelineShaderStageCreateInfo}`
  * `groups::Vector{RayTracingShaderGroupCreateInfoKHR}`
  * `max_pipeline_ray_recursion_depth::UInt32`
  * `layout::PipelineLayout`
  * `base_pipeline_index::Int32`
  * `next::Any`: defaults to `C_NULL`
  * `flags::PipelineCreateFlag`: defaults to `0`
  * `library_info::PipelineLibraryCreateInfoKHR`: defaults to `C_NULL`
  * `library_interface::RayTracingPipelineInterfaceCreateInfoKHR`: defaults to `C_NULL`
  * `dynamic_state::PipelineDynamicStateCreateInfo`: defaults to `C_NULL`
  * `base_pipeline_handle::Pipeline`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineCreateInfoKHR.html)

```julia
RayTracingPipelineCreateInfoKHR(
    stages::AbstractArray,
    groups::AbstractArray,
    max_pipeline_ray_recursion_depth::Integer,
    layout::Vulkan.PipelineLayout,
    base_pipeline_index::Integer;
    next,
    flags,
    library_info,
    library_interface,
    dynamic_state,
    base_pipeline_handle
) -> Vulkan.RayTracingPipelineCreateInfoKHR

```
