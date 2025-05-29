Arguments:

  * `wait_semaphore_infos::Vector{SemaphoreSubmitInfo}`
  * `command_buffer_infos::Vector{CommandBufferSubmitInfo}`
  * `signal_semaphore_infos::Vector{SemaphoreSubmitInfo}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::SubmitFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubmitInfo2.html)

```julia
SubmitInfo2(
    wait_semaphore_infos::AbstractArray,
    command_buffer_infos::AbstractArray,
    signal_semaphore_infos::AbstractArray;
    next,
    flags
) -> Vulkan.SubmitInfo2

```
