拡張: VK*NV*ray_tracing

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst::AccelerationStructureNV`
  * `src::AccelerationStructureNV`
  * `mode::CopyAccelerationStructureModeKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyAccelerationStructureNV.html)

```julia
cmd_copy_acceleration_structure_nv(
    command_buffer,
    dst,
    src,
    mode::Vulkan.CopyAccelerationStructureModeKHR
)

```
