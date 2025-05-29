拡張: VK*EXT*multi_draw

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `index_info::Vector{_MultiDrawIndexedInfoEXT}`
  * `instance_count::UInt32`
  * `first_instance::UInt32`
  * `stride::UInt32`
  * `vertex_offset::Int32`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdDrawMultiIndexedEXT.html)

```julia
_cmd_draw_multi_indexed_ext(
    command_buffer,
    index_info::AbstractArray,
    instance_count::Integer,
    first_instance::Integer,
    stride::Integer;
    vertex_offset
)

```
