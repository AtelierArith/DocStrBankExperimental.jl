拡張: VK*AMD*buffer_marker

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `dst_buffer::Buffer`
  * `dst_offset::UInt64`
  * `marker::UInt32`
  * `pipeline_stage::PipelineStageFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWriteBufferMarkerAMD.html)

```julia
_cmd_write_buffer_marker_amd(
    command_buffer,
    dst_buffer,
    dst_offset::Integer,
    marker::Integer;
    pipeline_stage
)

```
