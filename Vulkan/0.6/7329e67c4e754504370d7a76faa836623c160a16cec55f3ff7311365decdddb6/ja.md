拡張: VK*NV*mesh_shader

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `buffer::Buffer`
  * `offset::UInt64`
  * `draw_count::UInt32`
  * `stride::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawMeshTasksIndirectNV.html)

```julia
cmd_draw_mesh_tasks_indirect_nv(
    command_buffer,
    buffer,
    offset::Integer,
    draw_count::Integer,
    stride::Integer
)

```
