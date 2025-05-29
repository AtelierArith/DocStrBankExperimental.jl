Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `pipeline_stage::PipelineStageFlag`
  * `query_pool::QueryPool`
  * `query::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteTimestamp.html)

```julia
cmd_write_timestamp(
    command_buffer,
    pipeline_stage::Vulkan.PipelineStageFlag,
    query_pool,
    query::Integer
)

```
