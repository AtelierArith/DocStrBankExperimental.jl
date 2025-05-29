引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `base_group_x::UInt32`
  * `base_group_y::UInt32`
  * `base_group_z::UInt32`
  * `group_count_x::UInt32`
  * `group_count_y::UInt32`
  * `group_count_z::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDispatchBase.html)

```julia
cmd_dispatch_base(
    command_buffer,
    base_group_x::Integer,
    base_group_y::Integer,
    base_group_z::Integer,
    group_count_x::Integer,
    group_count_y::Integer,
    group_count_z::Integer
)

```
