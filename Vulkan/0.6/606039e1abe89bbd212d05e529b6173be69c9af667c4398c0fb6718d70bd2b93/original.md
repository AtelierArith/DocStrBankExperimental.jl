Extension: VK_EXT_mesh_shader

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `buffer::Buffer`
  * `offset::UInt64`
  * `count_buffer::Buffer`
  * `count_buffer_offset::UInt64`
  * `max_draw_count::UInt32`
  * `stride::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawMeshTasksIndirectCountEXT.html)

```julia
cmd_draw_mesh_tasks_indirect_count_ext(
    command_buffer,
    buffer,
    offset::Integer,
    count_buffer,
    count_buffer_offset::Integer,
    max_draw_count::Integer,
    stride::Integer
)

```
