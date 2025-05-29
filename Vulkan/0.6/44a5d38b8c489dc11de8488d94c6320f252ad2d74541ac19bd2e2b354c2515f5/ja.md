引数:

  * `semaphores::Vector{Semaphore}`
  * `values::Vector{UInt64}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::SemaphoreWaitFlag`: デフォルトは `0`

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreWaitInfo.html)

```julia
_SemaphoreWaitInfo(
    semaphores::AbstractArray,
    values::AbstractArray;
    next,
    flags
) -> Vulkan._SemaphoreWaitInfo

```
