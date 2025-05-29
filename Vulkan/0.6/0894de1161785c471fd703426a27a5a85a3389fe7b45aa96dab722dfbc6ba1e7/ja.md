VkAccelerationStructureInstanceKHRの高レベルラッパー。

拡張: VK*KHR*acceleration_structure

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureInstanceKHR.html)

```julia
struct AccelerationStructureInstanceKHR <: Vulkan.HighLevelStruct
```

  * `transform::Vulkan.TransformMatrixKHR`
  * `instance_custom_index::UInt32`
  * `mask::UInt32`
  * `instance_shader_binding_table_record_offset::UInt32`
  * `flags::Vulkan.GeometryInstanceFlagKHR`
  * `acceleration_structure_reference::UInt64`
