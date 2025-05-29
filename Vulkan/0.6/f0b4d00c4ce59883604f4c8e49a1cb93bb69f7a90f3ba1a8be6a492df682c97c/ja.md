VkRayTracingShaderGroupCreateInfoNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingShaderGroupCreateInfoNV.html)

```julia
struct RayTracingShaderGroupCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.RayTracingShaderGroupTypeKHR`
  * `general_shader::UInt32`
  * `closest_hit_shader::UInt32`
  * `any_hit_shader::UInt32`
  * `intersection_shader::UInt32`
