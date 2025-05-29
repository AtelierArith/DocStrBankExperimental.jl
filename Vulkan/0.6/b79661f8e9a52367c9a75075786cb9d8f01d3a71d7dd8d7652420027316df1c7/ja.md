拡張: VK*KHR*acceleration_structure

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `infos::Vector{_AccelerationStructureBuildGeometryInfoKHR}`
  * `indirect_device_addresses::Vector{UInt64}`
  * `indirect_strides::Vector{UInt32}`
  * `max_primitive_counts::Vector{UInt32}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBuildAccelerationStructuresIndirectKHR.html)

```julia
_cmd_build_acceleration_structures_indirect_khr(
    command_buffer,
    infos::AbstractArray,
    indirect_device_addresses::AbstractArray,
    indirect_strides::AbstractArray,
    max_primitive_counts::AbstractArray
)

```
