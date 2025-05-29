VkPhysicalDeviceMeshShaderPropertiesNVの高レベルラッパー。

拡張: VK*NV*mesh_shader

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMeshShaderPropertiesNV.html)

```julia
struct PhysicalDeviceMeshShaderPropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_draw_mesh_tasks_count::UInt32`
  * `max_task_work_group_invocations::UInt32`
  * `max_task_work_group_size::Tuple{UInt32, UInt32, UInt32}`
  * `max_task_total_memory_size::UInt32`
  * `max_task_output_count::UInt32`
  * `max_mesh_work_group_invocations::UInt32`
  * `max_mesh_work_group_size::Tuple{UInt32, UInt32, UInt32}`
  * `max_mesh_total_memory_size::UInt32`
  * `max_mesh_output_vertices::UInt32`
  * `max_mesh_output_primitives::UInt32`
  * `max_mesh_multiview_view_count::UInt32`
  * `mesh_output_per_vertex_granularity::UInt32`
  * `mesh_output_per_primitive_granularity::UInt32`
