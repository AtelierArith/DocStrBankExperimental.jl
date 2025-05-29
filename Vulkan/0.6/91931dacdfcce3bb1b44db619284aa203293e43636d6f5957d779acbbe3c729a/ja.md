VkQueryPoolPerformanceCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*performance_query

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolPerformanceCreateInfoKHR.html)

```julia
struct QueryPoolPerformanceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `queue_family_index::UInt32`
  * `counter_indices::Vector{UInt32}`
