Extension: VK_AMD_buffer_marker

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `marker::UInt32`
  * `pipeline_stage::PipelineStageFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteBufferMarkerAMD.html)

```julia
cmd_write_buffer_marker_amd(
    command_buffer,
    dst_buffer,
    dst_offset::Integer,
    marker::Integer;
    pipeline_stage
)

```
