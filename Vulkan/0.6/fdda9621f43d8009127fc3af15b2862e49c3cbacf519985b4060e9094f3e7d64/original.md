Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `wait_semaphore_values::Vector{UInt64}`: defaults to `C_NULL`
  * `signal_semaphore_values::Vector{UInt64}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkTimelineSemaphoreSubmitInfo.html)

```julia
_TimelineSemaphoreSubmitInfo(
;
    next,
    wait_semaphore_values,
    signal_semaphore_values
) -> Vulkan._TimelineSemaphoreSubmitInfo

```
