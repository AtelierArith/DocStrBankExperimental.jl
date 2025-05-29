Extension: VK_KHR_acceleration_structure

Arguments:

  * `device::Device`
  * `build_type::AccelerationStructureBuildTypeKHR`
  * `build_info::AccelerationStructureBuildGeometryInfoKHR`
  * `max_primitive_counts::Vector{UInt32}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureBuildSizesKHR.html)

```julia
get_acceleration_structure_build_sizes_khr(
    device,
    build_type::Vulkan.AccelerationStructureBuildTypeKHR,
    build_info::Vulkan.AccelerationStructureBuildGeometryInfoKHR;
    max_primitive_counts
) -> Vulkan.AccelerationStructureBuildSizesInfoKHR

```
