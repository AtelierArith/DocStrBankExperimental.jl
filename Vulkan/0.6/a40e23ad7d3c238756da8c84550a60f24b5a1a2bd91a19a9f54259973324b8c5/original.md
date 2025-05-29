Extension: VK_KHR_ray_tracing_pipeline

Arguments:

  * `ray_tracing_pipeline::Bool`
  * `ray_tracing_pipeline_shader_group_handle_capture_replay::Bool`
  * `ray_tracing_pipeline_shader_group_handle_capture_replay_mixed::Bool`
  * `ray_tracing_pipeline_trace_rays_indirect::Bool`
  * `ray_traversal_primitive_culling::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPipelineFeaturesKHR.html)

```julia
_PhysicalDeviceRayTracingPipelineFeaturesKHR(
    ray_tracing_pipeline::Bool,
    ray_tracing_pipeline_shader_group_handle_capture_replay::Bool,
    ray_tracing_pipeline_shader_group_handle_capture_replay_mixed::Bool,
    ray_tracing_pipeline_trace_rays_indirect::Bool,
    ray_traversal_primitive_culling::Bool;
    next
) -> Vulkan._PhysicalDeviceRayTracingPipelineFeaturesKHR

```
