引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `memory_barriers::Vector{_MemoryBarrier}`
  * `buffer_memory_barriers::Vector{_BufferMemoryBarrier}`
  * `image_memory_barriers::Vector{_ImageMemoryBarrier}`
  * `src_stage_mask::PipelineStageFlag`: デフォルトは `0`
  * `dst_stage_mask::PipelineStageFlag`: デフォルトは `0`
  * `dependency_flags::DependencyFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdPipelineBarrier.html)

```julia
_cmd_pipeline_barrier(
    command_buffer,
    memory_barriers::AbstractArray,
    buffer_memory_barriers::AbstractArray,
    image_memory_barriers::AbstractArray;
    src_stage_mask,
    dst_stage_mask,
    dependency_flags
)

```
