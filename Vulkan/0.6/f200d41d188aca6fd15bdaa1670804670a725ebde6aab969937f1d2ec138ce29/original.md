Extension: VK_EXT_transform_feedback

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `instance_count::UInt32`
  * `first_instance::UInt32`
  * `counter_buffer::Buffer`
  * `counter_buffer_offset::UInt64`
  * `counter_offset::UInt32`
  * `vertex_stride::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawIndirectByteCountEXT.html)

```julia
cmd_draw_indirect_byte_count_ext(
    command_buffer,
    instance_count::Integer,
    first_instance::Integer,
    counter_buffer,
    counter_buffer_offset::Integer,
    counter_offset::Integer,
    vertex_stride::Integer
)

```
