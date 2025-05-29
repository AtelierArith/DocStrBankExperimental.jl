引数:

  * `semaphores::Vector{Semaphore}`
  * `values::Vector{UInt64}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::SemaphoreWaitFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreWaitInfo.html)

```julia
SemaphoreWaitInfo(
    semaphores::AbstractArray,
    values::AbstractArray;
    next,
    flags
) -> Vulkan.SemaphoreWaitInfo

```
