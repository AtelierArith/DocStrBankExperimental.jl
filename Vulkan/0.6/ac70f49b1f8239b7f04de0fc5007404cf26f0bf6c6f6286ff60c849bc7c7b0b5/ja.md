VkPhysicalDeviceRayTracingPropertiesNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceRayTracingPropertiesNV.html)

```julia
struct PhysicalDeviceRayTracingPropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shader_group_handle_size::UInt32`
  * `max_recursion_depth::UInt32`
  * `max_shader_group_stride::UInt32`
  * `shader_group_base_alignment::UInt32`
  * `max_geometry_count::UInt64`
  * `max_instance_count::UInt64`
  * `max_triangle_count::UInt64`
  * `max_descriptor_set_acceleration_structures::UInt32`
