拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `stages::Vector{_PipelineShaderStageCreateInfo}`
  * `groups::Vector{_RayTracingShaderGroupCreateInfoKHR}`
  * `max_pipeline_ray_recursion_depth::UInt32`
  * `layout::PipelineLayout`
  * `base_pipeline_index::Int32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::PipelineCreateFlag`: デフォルトは `0`
  * `library_info::_PipelineLibraryCreateInfoKHR`: デフォルトは `C_NULL`
  * `library_interface::_RayTracingPipelineInterfaceCreateInfoKHR`: デフォルトは `C_NULL`
  * `dynamic_state::_PipelineDynamicStateCreateInfo`: デフォルトは `C_NULL`
  * `base_pipeline_handle::Pipeline`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineCreateInfoKHR.html)

```julia
_RayTracingPipelineCreateInfoKHR(
    stages::AbstractArray,
    groups::AbstractArray,
    max_pipeline_ray_recursion_depth::Integer,
    layout,
    base_pipeline_index::Integer;
    next,
    flags,
    library_info,
    library_interface,
    dynamic_state,
    base_pipeline_handle
) -> Vulkan._RayTracingPipelineCreateInfoKHR

```
