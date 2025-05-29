Extension: VK_NV_ray_tracing

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst::AccelerationStructureNV`
  * `src::AccelerationStructureNV`
  * `mode::CopyAccelerationStructureModeKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyAccelerationStructureNV.html)

```julia
cmd_copy_acceleration_structure_nv(
    command_buffer,
    dst,
    src,
    mode::Vulkan.CopyAccelerationStructureModeKHR
)

```
