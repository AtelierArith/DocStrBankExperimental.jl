Extension: VK_KHR_performance_query

Arguments:

  * `timeout::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::AcquireProfilingLockFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireProfilingLockInfoKHR.html)

```julia
_AcquireProfilingLockInfoKHR(
    timeout::Integer;
    next,
    flags
) -> Vulkan._AcquireProfilingLockInfoKHR

```
