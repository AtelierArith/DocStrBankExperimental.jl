拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `shader_group_handle_size::UInt32`
  * `max_ray_recursion_depth::UInt32`
  * `max_shader_group_stride::UInt32`
  * `shader_group_base_alignment::UInt32`
  * `shader_group_handle_capture_replay_size::UInt32`
  * `max_ray_dispatch_invocation_count::UInt32`
  * `shader_group_handle_alignment::UInt32`
  * `max_ray_hit_attribute_size::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPipelinePropertiesKHR.html)

```julia
_PhysicalDeviceRayTracingPipelinePropertiesKHR(
    shader_group_handle_size::Integer,
    max_ray_recursion_depth::Integer,
    max_shader_group_stride::Integer,
    shader_group_base_alignment::Integer,
    shader_group_handle_capture_replay_size::Integer,
    max_ray_dispatch_invocation_count::Integer,
    shader_group_handle_alignment::Integer,
    max_ray_hit_attribute_size::Integer;
    next
) -> Vulkan._PhysicalDeviceRayTracingPipelinePropertiesKHR

```
