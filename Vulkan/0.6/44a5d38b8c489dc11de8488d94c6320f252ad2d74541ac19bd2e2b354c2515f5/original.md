Arguments:

  * `semaphores::Vector{Semaphore}`
  * `values::Vector{UInt64}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::SemaphoreWaitFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreWaitInfo.html)

```julia
_SemaphoreWaitInfo(
    semaphores::AbstractArray,
    values::AbstractArray;
    next,
    flags
) -> Vulkan._SemaphoreWaitInfo

```
