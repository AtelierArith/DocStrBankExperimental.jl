Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `query_pool::QueryPool`
  * `query::UInt32`
  * `stage::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteTimestamp2.html)

```julia
_cmd_write_timestamp_2(
    command_buffer,
    query_pool,
    query::Integer;
    stage
)

```
