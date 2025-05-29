High-level wrapper for VkQueryPoolPerformanceCreateInfoKHR.

Extension: VK_KHR_performance_query

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolPerformanceCreateInfoKHR.html)

```julia
struct QueryPoolPerformanceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `queue_family_index::UInt32`
  * `counter_indices::Vector{UInt32}`
