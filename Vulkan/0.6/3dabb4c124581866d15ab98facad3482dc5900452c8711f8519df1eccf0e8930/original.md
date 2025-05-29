Extension: VK_NV_ray_tracing

Arguments:

  * `type::RayTracingShaderGroupTypeKHR`
  * `general_shader::UInt32`
  * `closest_hit_shader::UInt32`
  * `any_hit_shader::UInt32`
  * `intersection_shader::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingShaderGroupCreateInfoNV.html)

```julia
RayTracingShaderGroupCreateInfoNV(
    type::Vulkan.RayTracingShaderGroupTypeKHR,
    general_shader::Integer,
    closest_hit_shader::Integer,
    any_hit_shader::Integer,
    intersection_shader::Integer;
    next
) -> Vulkan.RayTracingShaderGroupCreateInfoNV

```
