Arguments:

  * `semaphore::Semaphore`
  * `value::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSignalInfo.html)

```julia
SemaphoreSignalInfo(
    semaphore::Vulkan.Semaphore,
    value::Integer;
    next
) -> Vulkan.SemaphoreSignalInfo

```
