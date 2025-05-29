Extension: VK_EXT_mesh_shader

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `buffer::Buffer`
  * `offset::UInt64`
  * `draw_count::UInt32`
  * `stride::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawMeshTasksIndirectEXT.html)

```julia
cmd_draw_mesh_tasks_indirect_ext(
    command_buffer,
    buffer,
    offset::Integer,
    draw_count::Integer,
    stride::Integer
)

```
