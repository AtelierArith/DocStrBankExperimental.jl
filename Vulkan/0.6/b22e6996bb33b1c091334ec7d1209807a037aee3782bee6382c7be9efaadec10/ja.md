VkPhysicalDeviceAccelerationStructurePropertiesKHRの高レベルラッパー。

拡張: VK*KHR*acceleration_structure

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceAccelerationStructurePropertiesKHR.html)

```julia
struct PhysicalDeviceAccelerationStructurePropertiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `max_geometry_count::UInt64`
  * `max_instance_count::UInt64`
  * `max_primitive_count::UInt64`
  * `max_per_stage_descriptor_acceleration_structures::UInt32`
  * `max_per_stage_descriptor_update_after_bind_acceleration_structures::UInt32`
  * `max_descriptor_set_acceleration_structures::UInt32`
  * `max_descriptor_set_update_after_bind_acceleration_structures::UInt32`
  * `min_acceleration_structure_scratch_offset_alignment::UInt32`
