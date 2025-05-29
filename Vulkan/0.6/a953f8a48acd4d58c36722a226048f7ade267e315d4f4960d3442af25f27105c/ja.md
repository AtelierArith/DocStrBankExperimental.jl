拡張: VK*EXT*multi_draw

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `vertex_info::Vector{MultiDrawInfoEXT}`
  * `instance_count::UInt32`
  * `first_instance::UInt32`
  * `stride::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawMultiEXT.html)

```julia
cmd_draw_multi_ext(
    command_buffer,
    vertex_info::AbstractArray,
    instance_count::Integer,
    first_instance::Integer,
    stride::Integer
)

```
