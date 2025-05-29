引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `query_pool::QueryPool`
  * `query::UInt32`
  * `flags::QueryControlFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBeginQuery.html)

```julia
_cmd_begin_query(
    command_buffer,
    query_pool,
    query::Integer;
    flags
)

```
