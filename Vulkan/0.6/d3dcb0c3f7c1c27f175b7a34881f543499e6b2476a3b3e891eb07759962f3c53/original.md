High-level wrapper for VkPerformanceCounterKHR.

Extension: VK_KHR_performance_query

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterKHR.html)

```julia
struct PerformanceCounterKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `unit::Vulkan.PerformanceCounterUnitKHR`
  * `scope::Vulkan.PerformanceCounterScopeKHR`
  * `storage::Vulkan.PerformanceCounterStorageKHR`
  * `uuid::NTuple{16, UInt8}`
