高レベルのラッパー VkRayTracingShaderGroupCreateInfoKHR。

拡張: VK*KHR*ray*tracing*pipeline

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingShaderGroupCreateInfoKHR.html)

```julia
struct RayTracingShaderGroupCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.RayTracingShaderGroupTypeKHR`
  * `general_shader::UInt32`
  * `closest_hit_shader::UInt32`
  * `any_hit_shader::UInt32`
  * `intersection_shader::UInt32`
  * `shader_group_capture_replay_handle::Ptr{Nothing}`
