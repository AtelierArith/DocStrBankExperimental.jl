Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `size::UInt64`
  * `data::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdFillBuffer.html)

```julia
cmd_fill_buffer(
    command_buffer,
    dst_buffer,
    dst_offset::Integer,
    size::Integer,
    data::Integer
)

```
