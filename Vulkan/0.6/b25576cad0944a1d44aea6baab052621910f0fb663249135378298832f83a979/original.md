Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `memory_barriers::Vector{MemoryBarrier}`
  * `buffer_memory_barriers::Vector{BufferMemoryBarrier}`
  * `image_memory_barriers::Vector{ImageMemoryBarrier}`
  * `src_stage_mask::PipelineStageFlag`: defaults to `0`
  * `dst_stage_mask::PipelineStageFlag`: defaults to `0`
  * `dependency_flags::DependencyFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdPipelineBarrier.html)

```julia
cmd_pipeline_barrier(
    command_buffer,
    memory_barriers::AbstractArray,
    buffer_memory_barriers::AbstractArray,
    image_memory_barriers::AbstractArray;
    src_stage_mask,
    dst_stage_mask,
    dependency_flags
)

```
