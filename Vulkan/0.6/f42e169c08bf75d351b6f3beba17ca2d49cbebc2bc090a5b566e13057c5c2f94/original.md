Extension: VK_KHR_acceleration_structure

Arguments:

  * `type::AccelerationStructureTypeKHR`
  * `mode::BuildAccelerationStructureModeKHR`
  * `scratch_data::_DeviceOrHostAddressKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::BuildAccelerationStructureFlagKHR`: defaults to `0`
  * `src_acceleration_structure::AccelerationStructureKHR`: defaults to `C_NULL`
  * `dst_acceleration_structure::AccelerationStructureKHR`: defaults to `C_NULL`
  * `geometries::Vector{_AccelerationStructureGeometryKHR}`: defaults to `C_NULL`
  * `geometries_2::Vector{_AccelerationStructureGeometryKHR}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildGeometryInfoKHR.html)

```julia
_AccelerationStructureBuildGeometryInfoKHR(
    type::Vulkan.AccelerationStructureTypeKHR,
    mode::Vulkan.BuildAccelerationStructureModeKHR,
    scratch_data::Vulkan._DeviceOrHostAddressKHR;
    next,
    flags,
    src_acceleration_structure,
    dst_acceleration_structure,
    geometries,
    geometries_2
) -> Vulkan._AccelerationStructureBuildGeometryInfoKHR

```
