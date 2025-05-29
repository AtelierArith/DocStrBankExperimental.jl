拡張: VK*KHR*performance_query

引数:

  * `timeout::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::AcquireProfilingLockFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireProfilingLockInfoKHR.html)

```julia
_AcquireProfilingLockInfoKHR(
    timeout::Integer;
    next,
    flags
) -> Vulkan._AcquireProfilingLockInfoKHR

```
