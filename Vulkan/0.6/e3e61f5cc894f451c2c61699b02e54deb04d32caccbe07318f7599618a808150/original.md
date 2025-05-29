Extension: VK_NV_ray_tracing

Arguments:

  * `shader_group_handle_size::UInt32`
  * `max_recursion_depth::UInt32`
  * `max_shader_group_stride::UInt32`
  * `shader_group_base_alignment::UInt32`
  * `max_geometry_count::UInt64`
  * `max_instance_count::UInt64`
  * `max_triangle_count::UInt64`
  * `max_descriptor_set_acceleration_structures::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPropertiesNV.html)

```julia
_PhysicalDeviceRayTracingPropertiesNV(
    shader_group_handle_size::Integer,
    max_recursion_depth::Integer,
    max_shader_group_stride::Integer,
    shader_group_base_alignment::Integer,
    max_geometry_count::Integer,
    max_instance_count::Integer,
    max_triangle_count::Integer,
    max_descriptor_set_acceleration_structures::Integer;
    next
) -> Vulkan._PhysicalDeviceRayTracingPropertiesNV

```
