拡張: VK*KHR*acceleration_structure

引数:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::AccelerationStructureGeometryDataKHR`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::GeometryFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryKHR.html)

```julia
AccelerationStructureGeometryKHR(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan.AccelerationStructureGeometryDataKHR;
    next,
    flags
) -> Vulkan.AccelerationStructureGeometryKHR

```
