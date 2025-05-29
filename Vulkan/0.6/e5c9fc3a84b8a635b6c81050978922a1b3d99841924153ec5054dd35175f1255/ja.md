拡張: VK*KHR*ray*tracing*pipeline

引数:

  * `type::RayTracingShaderGroupTypeKHR`
  * `general_shader::UInt32`
  * `closest_hit_shader::UInt32`
  * `any_hit_shader::UInt32`
  * `intersection_shader::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `shader_group_capture_replay_handle::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingShaderGroupCreateInfoKHR.html)

```julia
RayTracingShaderGroupCreateInfoKHR(
    type::Vulkan.RayTracingShaderGroupTypeKHR,
    general_shader::Integer,
    closest_hit_shader::Integer,
    any_hit_shader::Integer,
    intersection_shader::Integer;
    next,
    shader_group_capture_replay_handle
) -> Vulkan.RayTracingShaderGroupCreateInfoKHR

```
