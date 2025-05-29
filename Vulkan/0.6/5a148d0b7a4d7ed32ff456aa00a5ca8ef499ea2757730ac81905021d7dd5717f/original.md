Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `data_size::UInt64`
  * `data::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdUpdateBuffer.html)

```julia
_cmd_update_buffer(
    command_buffer,
    dst_buffer,
    dst_offset::Integer,
    data_size::Integer,
    data::Ptr{Nothing}
)

```
