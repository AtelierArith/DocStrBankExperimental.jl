拡張: VK*EXT*mesh_shader

引数:

  * `max_task_work_group_total_count::UInt32`
  * `max_task_work_group_count::NTuple{3, UInt32}`
  * `max_task_work_group_invocations::UInt32`
  * `max_task_work_group_size::NTuple{3, UInt32}`
  * `max_task_payload_size::UInt32`
  * `max_task_shared_memory_size::UInt32`
  * `max_task_payload_and_shared_memory_size::UInt32`
  * `max_mesh_work_group_total_count::UInt32`
  * `max_mesh_work_group_count::NTuple{3, UInt32}`
  * `max_mesh_work_group_invocations::UInt32`
  * `max_mesh_work_group_size::NTuple{3, UInt32}`
  * `max_mesh_shared_memory_size::UInt32`
  * `max_mesh_payload_and_shared_memory_size::UInt32`
  * `max_mesh_output_memory_size::UInt32`
  * `max_mesh_payload_and_output_memory_size::UInt32`
  * `max_mesh_output_components::UInt32`
  * `max_mesh_output_vertices::UInt32`
  * `max_mesh_output_primitives::UInt32`
  * `max_mesh_output_layers::UInt32`
  * `max_mesh_multiview_view_count::UInt32`
  * `mesh_output_per_vertex_granularity::UInt32`
  * `mesh_output_per_primitive_granularity::UInt32`
  * `max_preferred_task_work_group_invocations::UInt32`
  * `max_preferred_mesh_work_group_invocations::UInt32`
  * `prefers_local_invocation_vertex_output::Bool`
  * `prefers_local_invocation_primitive_output::Bool`
  * `prefers_compact_vertex_output::Bool`
  * `prefers_compact_primitive_output::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMeshShaderPropertiesEXT.html)

```julia
_PhysicalDeviceMeshShaderPropertiesEXT(
    max_task_work_group_total_count::Integer,
    max_task_work_group_count::Tuple{UInt32, UInt32, UInt32},
    max_task_work_group_invocations::Integer,
    max_task_work_group_size::Tuple{UInt32, UInt32, UInt32},
    max_task_payload_size::Integer,
    max_task_shared_memory_size::Integer,
    max_task_payload_and_shared_memory_size::Integer,
    max_mesh_work_group_total_count::Integer,
    max_mesh_work_group_count::Tuple{UInt32, UInt32, UInt32},
    max_mesh_work_group_invocations::Integer,
    max_mesh_work_group_size::Tuple{UInt32, UInt32, UInt32},
    max_mesh_shared_memory_size::Integer,
    max_mesh_payload_and_shared_memory_size::Integer,
    max_mesh_output_memory_size::Integer,
    max_mesh_payload_and_output_memory_size::Integer,
    max_mesh_output_components::Integer,
    max_mesh_output_vertices::Integer,
    max_mesh_output_primitives::Integer,
    max_mesh_output_layers::Integer,
    max_mesh_multiview_view_count::Integer,
    mesh_output_per_vertex_granularity::Integer,
    mesh_output_per_primitive_granularity::Integer,
    max_preferred_task_work_group_invocations::Integer,
    max_preferred_mesh_work_group_invocations::Integer,
    prefers_local_invocation_vertex_output::Bool,
    prefers_local_invocation_primitive_output::Bool,
    prefers_compact_vertex_output::Bool,
    prefers_compact_primitive_output::Bool;
    next
) -> Vulkan._PhysicalDeviceMeshShaderPropertiesEXT

```
