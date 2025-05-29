Extension: VK_EXT_transform_feedback

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `query_pool::QueryPool`
  * `query::UInt32`
  * `index::UInt32`
  * `flags::QueryControlFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBeginQueryIndexedEXT.html)

```julia
cmd_begin_query_indexed_ext(
    command_buffer,
    query_pool,
    query::Integer,
    index::Integer;
    flags
)

```
