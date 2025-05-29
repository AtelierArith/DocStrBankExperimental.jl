拡張: VK*KHR*acceleration_structure

引数:

  * `device::Device`
  * `build_type::AccelerationStructureBuildTypeKHR`
  * `build_info::_AccelerationStructureBuildGeometryInfoKHR`
  * `max_primitive_counts::Vector{UInt32}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureBuildSizesKHR.html)

```julia
_get_acceleration_structure_build_sizes_khr(
    device,
    build_type::Vulkan.AccelerationStructureBuildTypeKHR,
    build_info::Vulkan._AccelerationStructureBuildGeometryInfoKHR;
    max_primitive_counts
) -> Vulkan._AccelerationStructureBuildSizesInfoKHR

```
