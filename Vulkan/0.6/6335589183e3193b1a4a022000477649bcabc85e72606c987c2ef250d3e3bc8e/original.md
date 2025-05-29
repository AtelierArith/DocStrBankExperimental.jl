Arguments:

  * `semaphore::Semaphore`
  * `value::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSignalInfo.html)

```julia
_SemaphoreSignalInfo(
    semaphore,
    value::Integer;
    next
) -> Vulkan._SemaphoreSignalInfo

```
