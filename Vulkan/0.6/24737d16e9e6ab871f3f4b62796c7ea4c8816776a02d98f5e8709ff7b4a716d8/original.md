Extension: VK_KHR_performance_query

Arguments:

  * `timeout::UInt64`
  * `next::Any`: defaults to `C_NULL`
  * `flags::AcquireProfilingLockFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireProfilingLockInfoKHR.html)

```julia
AcquireProfilingLockInfoKHR(
    timeout::Integer;
    next,
    flags
) -> Vulkan.AcquireProfilingLockInfoKHR

```
