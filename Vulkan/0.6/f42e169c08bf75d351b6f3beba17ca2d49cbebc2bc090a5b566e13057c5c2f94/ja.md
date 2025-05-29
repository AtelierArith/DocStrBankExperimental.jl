拡張: VK*KHR*acceleration_structure

引数:

  * `type::AccelerationStructureTypeKHR`
  * `mode::BuildAccelerationStructureModeKHR`
  * `scratch_data::_DeviceOrHostAddressKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::BuildAccelerationStructureFlagKHR`: デフォルトは `0`
  * `src_acceleration_structure::AccelerationStructureKHR`: デフォルトは `C_NULL`
  * `dst_acceleration_structure::AccelerationStructureKHR`: デフォルトは `C_NULL`
  * `geometries::Vector{_AccelerationStructureGeometryKHR}`: デフォルトは `C_NULL`
  * `geometries_2::Vector{_AccelerationStructureGeometryKHR}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildGeometryInfoKHR.html)

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
