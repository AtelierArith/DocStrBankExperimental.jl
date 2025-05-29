High-level wrapper for VkPerformanceOverrideInfoINTEL.

Extension: VK_INTEL_performance_query

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceOverrideInfoINTEL.html)

```julia
struct PerformanceOverrideInfoINTEL <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.PerformanceOverrideTypeINTEL`
  * `enable::Bool`
  * `parameter::UInt64`
