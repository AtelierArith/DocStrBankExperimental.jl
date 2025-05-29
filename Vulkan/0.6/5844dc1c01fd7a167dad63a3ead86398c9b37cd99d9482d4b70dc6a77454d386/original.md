High-level wrapper for VkAccelerationStructureSRTMotionInstanceNV.

Extension: VK_NV_ray_tracing_motion_blur

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureSRTMotionInstanceNV.html)

```julia
struct AccelerationStructureSRTMotionInstanceNV <: Vulkan.HighLevelStruct
```

  * `transform_t_0::Vulkan.SRTDataNV`
  * `transform_t_1::Vulkan.SRTDataNV`
  * `instance_custom_index::UInt32`
  * `mask::UInt32`
  * `instance_shader_binding_table_record_offset::UInt32`
  * `flags::Vulkan.GeometryInstanceFlagKHR`
  * `acceleration_structure_reference::UInt64`
