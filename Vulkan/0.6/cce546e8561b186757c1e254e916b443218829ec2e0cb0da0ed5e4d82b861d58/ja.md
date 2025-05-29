VkPerformanceCounterDescriptionKHRの高レベルラッパー。

拡張: VK*KHR*performance_query

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterDescriptionKHR.html)

```julia
struct PerformanceCounterDescriptionKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PerformanceCounterDescriptionFlagKHR`
  * `name::String`
  * `category::String`
  * `description::String`
