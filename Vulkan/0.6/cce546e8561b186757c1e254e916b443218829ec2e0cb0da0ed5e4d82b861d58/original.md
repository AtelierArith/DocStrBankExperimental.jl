High-level wrapper for VkPerformanceCounterDescriptionKHR.

Extension: VK_KHR_performance_query

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterDescriptionKHR.html)

```julia
struct PerformanceCounterDescriptionKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PerformanceCounterDescriptionFlagKHR`
  * `name::String`
  * `category::String`
  * `description::String`
