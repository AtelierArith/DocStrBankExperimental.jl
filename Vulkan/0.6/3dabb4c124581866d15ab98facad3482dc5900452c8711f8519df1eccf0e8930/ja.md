拡張: VK*NV*ray_tracing

引数:

  * `type::RayTracingShaderGroupTypeKHR`
  * `general_shader::UInt32`
  * `closest_hit_shader::UInt32`
  * `any_hit_shader::UInt32`
  * `intersection_shader::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingShaderGroupCreateInfoNV.html)

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
