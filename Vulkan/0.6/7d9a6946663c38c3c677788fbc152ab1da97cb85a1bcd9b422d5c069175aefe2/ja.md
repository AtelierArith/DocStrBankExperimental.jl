VkPhysicalDeviceRayTracingPipelinePropertiesKHRの高レベルラッパー。

拡張: VK*KHR*ray*tracing*pipeline

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPipelinePropertiesKHR.html)

```julia
struct PhysicalDeviceRayTracingPipelinePropertiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shader_group_handle_size::UInt32`
  * `max_ray_recursion_depth::UInt32`
  * `max_shader_group_stride::UInt32`
  * `shader_group_base_alignment::UInt32`
  * `shader_group_handle_capture_replay_size::UInt32`
  * `max_ray_dispatch_invocation_count::UInt32`
  * `shader_group_handle_alignment::UInt32`
  * `max_ray_hit_attribute_size::UInt32`
