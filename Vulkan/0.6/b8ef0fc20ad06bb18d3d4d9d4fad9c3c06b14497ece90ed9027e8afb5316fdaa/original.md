Arguments:

  * `wait_semaphores::Vector{Semaphore}`
  * `wait_dst_stage_mask::Vector{PipelineStageFlag}`
  * `command_buffers::Vector{CommandBuffer}`
  * `signal_semaphores::Vector{Semaphore}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubmitInfo.html)

```julia
SubmitInfo(
    wait_semaphores::AbstractArray,
    wait_dst_stage_mask::AbstractArray,
    command_buffers::AbstractArray,
    signal_semaphores::AbstractArray;
    next
) -> Vulkan.SubmitInfo

```
