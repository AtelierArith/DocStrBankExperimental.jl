High-level wrapper for VkAcquireProfilingLockInfoKHR.

Extension: VK_KHR_performance_query

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireProfilingLockInfoKHR.html)

```julia
struct AcquireProfilingLockInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.AcquireProfilingLockFlagKHR`
  * `timeout::UInt64`
