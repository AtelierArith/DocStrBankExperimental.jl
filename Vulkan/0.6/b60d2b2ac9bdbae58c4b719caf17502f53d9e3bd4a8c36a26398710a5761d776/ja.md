拡張: VK*KHR*acceleration_structure

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `infos::Vector{AccelerationStructureBuildGeometryInfoKHR}`
  * `build_range_infos::Vector{AccelerationStructureBuildRangeInfoKHR}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBuildAccelerationStructuresKHR.html)

```julia
cmd_build_acceleration_structures_khr(
    command_buffer,
    infos::AbstractArray,
    build_range_infos::AbstractArray
)

```
