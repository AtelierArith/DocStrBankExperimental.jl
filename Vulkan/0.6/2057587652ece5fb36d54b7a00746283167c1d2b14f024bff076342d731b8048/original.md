Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `events::Vector{Event}`
  * `memory_barriers::Vector{MemoryBarrier}`
  * `buffer_memory_barriers::Vector{BufferMemoryBarrier}`
  * `image_memory_barriers::Vector{ImageMemoryBarrier}`
  * `src_stage_mask::PipelineStageFlag`: defaults to `0`
  * `dst_stage_mask::PipelineStageFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdWaitEvents.html)

```julia
cmd_wait_events(
    command_buffer,
    events::AbstractArray,
    memory_barriers::AbstractArray,
    buffer_memory_barriers::AbstractArray,
    image_memory_barriers::AbstractArray;
    src_stage_mask,
    dst_stage_mask
)

```
