Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `query_pool::QueryPool`
  * `first_query::UInt32`
  * `query_count::UInt32`
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `stride::UInt64`
  * `flags::QueryResultFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyQueryPoolResults.html)

```julia
cmd_copy_query_pool_results(
    command_buffer,
    query_pool,
    first_query::Integer,
    query_count::Integer,
    dst_buffer,
    dst_offset::Integer,
    stride::Integer;
    flags
)

```
