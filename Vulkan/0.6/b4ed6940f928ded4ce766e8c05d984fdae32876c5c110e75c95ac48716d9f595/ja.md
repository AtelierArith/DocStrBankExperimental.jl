拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `ray_tracing_pipeline::Bool`
  * `ray_tracing_pipeline_shader_group_handle_capture_replay::Bool`
  * `ray_tracing_pipeline_shader_group_handle_capture_replay_mixed::Bool`
  * `ray_tracing_pipeline_trace_rays_indirect::Bool`
  * `ray_traversal_primitive_culling::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPipelineFeaturesKHR.html)

```julia
PhysicalDeviceRayTracingPipelineFeaturesKHR(
    ray_tracing_pipeline::Bool,
    ray_tracing_pipeline_shader_group_handle_capture_replay::Bool,
    ray_tracing_pipeline_shader_group_handle_capture_replay_mixed::Bool,
    ray_tracing_pipeline_trace_rays_indirect::Bool,
    ray_traversal_primitive_culling::Bool;
    next
) -> Vulkan.PhysicalDeviceRayTracingPipelineFeaturesKHR

```
