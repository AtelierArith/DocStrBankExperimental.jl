High-level wrapper for VkRayTracingShaderGroupCreateInfoNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingShaderGroupCreateInfoNV.html)

```julia
struct RayTracingShaderGroupCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.RayTracingShaderGroupTypeKHR`
  * `general_shader::UInt32`
  * `closest_hit_shader::UInt32`
  * `any_hit_shader::UInt32`
  * `intersection_shader::UInt32`
