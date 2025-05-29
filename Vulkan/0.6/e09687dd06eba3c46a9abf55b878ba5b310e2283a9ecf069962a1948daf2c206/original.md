Arguments:

  * `wait_semaphore_infos::Vector{_SemaphoreSubmitInfo}`
  * `command_buffer_infos::Vector{_CommandBufferSubmitInfo}`
  * `signal_semaphore_infos::Vector{_SemaphoreSubmitInfo}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::SubmitFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubmitInfo2.html)

```julia
_SubmitInfo2(
    wait_semaphore_infos::AbstractArray,
    command_buffer_infos::AbstractArray,
    signal_semaphore_infos::AbstractArray;
    next,
    flags
) -> Vulkan._SubmitInfo2

```
