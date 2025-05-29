引数:

  * `semaphore::Semaphore`
  * `value::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSignalInfo.html)

```julia
SemaphoreSignalInfo(
    semaphore::Vulkan.Semaphore,
    value::Integer;
    next
) -> Vulkan.SemaphoreSignalInfo

```
