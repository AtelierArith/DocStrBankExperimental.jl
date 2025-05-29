拡張: VK*KHR*acceleration_structure

引数:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::_AccelerationStructureGeometryDataKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::GeometryFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryKHR.html)

```julia
_AccelerationStructureGeometryKHR(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan._AccelerationStructureGeometryDataKHR;
    next,
    flags
) -> Vulkan._AccelerationStructureGeometryKHR

```
