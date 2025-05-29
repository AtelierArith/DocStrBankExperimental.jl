VkPhysicalDeviceRayTracingPipelineFeaturesKHRの高レベルラッパー。

拡張: VK*KHR*ray*tracing*pipeline

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPipelineFeaturesKHR.html)

```julia
struct PhysicalDeviceRayTracingPipelineFeaturesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `ray_tracing_pipeline::Bool`
  * `ray_tracing_pipeline_shader_group_handle_capture_replay::Bool`
  * `ray_tracing_pipeline_shader_group_handle_capture_replay_mixed::Bool`
  * `ray_tracing_pipeline_trace_rays_indirect::Bool`
  * `ray_traversal_primitive_culling::Bool`
