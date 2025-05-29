引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `buffer::Buffer`
  * `offset::UInt64`
  * `count_buffer::Buffer`
  * `count_buffer_offset::UInt64`
  * `max_draw_count::UInt32`
  * `stride::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawIndirectCount.html)

```julia
cmd_draw_indirect_count(
    command_buffer,
    buffer,
    offset::Integer,
    count_buffer,
    count_buffer_offset::Integer,
    max_draw_count::Integer,
    stride::Integer
)

```
