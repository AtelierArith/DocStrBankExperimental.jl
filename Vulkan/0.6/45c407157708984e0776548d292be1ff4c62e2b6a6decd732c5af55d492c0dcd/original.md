Extension: VK_KHR_acceleration_structure

Arguments:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::_AccelerationStructureGeometryDataKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::GeometryFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryKHR.html)

```julia
_AccelerationStructureGeometryKHR(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan._AccelerationStructureGeometryDataKHR;
    next,
    flags
) -> Vulkan._AccelerationStructureGeometryKHR

```
