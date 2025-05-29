拡張: VK*NV*ray*tracing*motion_blur

引数:

  * `transform_t_0::_TransformMatrixKHR`
  * `transform_t_1::_TransformMatrixKHR`
  * `instance_custom_index::UInt32`
  * `mask::UInt32`
  * `instance_shader_binding_table_record_offset::UInt32`
  * `acceleration_structure_reference::UInt64`
  * `flags::GeometryInstanceFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureMatrixMotionInstanceNV.html)

```julia
_AccelerationStructureMatrixMotionInstanceNV(
    transform_t_0::Vulkan._TransformMatrixKHR,
    transform_t_1::Vulkan._TransformMatrixKHR,
    instance_custom_index::Integer,
    mask::Integer,
    instance_shader_binding_table_record_offset::Integer,
    acceleration_structure_reference::Integer;
    flags
)

```
