Arguments:

  * `semaphore::Semaphore`
  * `value::UInt64`
  * `device_index::UInt32`
  * `next::Any`: defaults to `C_NULL`
  * `stage_mask::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSubmitInfo.html)

```julia
SemaphoreSubmitInfo(
    semaphore::Vulkan.Semaphore,
    value::Integer,
    device_index::Integer;
    next,
    stage_mask
) -> Vulkan.SemaphoreSubmitInfo

```
