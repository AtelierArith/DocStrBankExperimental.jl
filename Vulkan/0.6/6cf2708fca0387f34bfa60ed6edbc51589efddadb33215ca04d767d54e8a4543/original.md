Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `query_pool::QueryPool`
  * `query::UInt32`
  * `flags::QueryControlFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBeginQuery.html)

```julia
cmd_begin_query(
    command_buffer,
    query_pool,
    query::Integer;
    flags
)

```
