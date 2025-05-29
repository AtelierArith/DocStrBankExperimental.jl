拡張: VK*NV*ray_tracing

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `info::_AccelerationStructureInfoNV`
  * `instance_offset::UInt64`
  * `update::Bool`
  * `dst::AccelerationStructureNV`
  * `scratch::Buffer`
  * `scratch_offset::UInt64`
  * `instance_data::Buffer`: デフォルトは `C_NULL`
  * `src::AccelerationStructureNV`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBuildAccelerationStructureNV.html)

```julia
_cmd_build_acceleration_structure_nv(
    command_buffer,
    info::Vulkan._AccelerationStructureInfoNV,
    instance_offset::Integer,
    update::Bool,
    dst,
    scratch,
    scratch_offset::Integer;
    instance_data,
    src
)

```
