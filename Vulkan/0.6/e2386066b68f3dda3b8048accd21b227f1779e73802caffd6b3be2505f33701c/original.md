Extension: VK_KHR_acceleration_structure

Arguments:

  * `geometry_type::GeometryTypeKHR`
  * `geometry::AccelerationStructureGeometryDataKHR`
  * `next::Any`: defaults to `C_NULL`
  * `flags::GeometryFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureGeometryKHR.html)

```julia
AccelerationStructureGeometryKHR(
    geometry_type::Vulkan.GeometryTypeKHR,
    geometry::Vulkan.AccelerationStructureGeometryDataKHR;
    next,
    flags
) -> Vulkan.AccelerationStructureGeometryKHR

```
