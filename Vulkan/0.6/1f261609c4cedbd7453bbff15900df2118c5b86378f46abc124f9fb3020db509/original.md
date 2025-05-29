Extension: VK_NV_ray_tracing

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `info::AccelerationStructureInfoNV`
  * `instance_offset::UInt64`
  * `update::Bool`
  * `dst::AccelerationStructureNV`
  * `scratch::Buffer`
  * `scratch_offset::UInt64`
  * `instance_data::Buffer`: defaults to `C_NULL`
  * `src::AccelerationStructureNV`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBuildAccelerationStructureNV.html)

```julia
cmd_build_acceleration_structure_nv(
    command_buffer,
    info::Vulkan.AccelerationStructureInfoNV,
    instance_offset::Integer,
    update::Bool,
    dst,
    scratch,
    scratch_offset::Integer;
    instance_data,
    src
)

```
