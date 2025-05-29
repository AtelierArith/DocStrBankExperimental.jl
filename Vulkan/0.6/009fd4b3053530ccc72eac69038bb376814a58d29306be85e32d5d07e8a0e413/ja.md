VkAccelerationStructureMatrixMotionInstanceNVの高レベルラッパー。

拡張: VK*NV*ray*tracing*motion_blur

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMatrixMotionInstanceNV.html)

```julia
struct AccelerationStructureMatrixMotionInstanceNV <: Vulkan.HighLevelStruct
```

  * `transform_t_0::Vulkan.TransformMatrixKHR`
  * `transform_t_1::Vulkan.TransformMatrixKHR`
  * `instance_custom_index::UInt32`
  * `mask::UInt32`
  * `instance_shader_binding_table_record_offset::UInt32`
  * `flags::Vulkan.GeometryInstanceFlagKHR`
  * `acceleration_structure_reference::UInt64`
