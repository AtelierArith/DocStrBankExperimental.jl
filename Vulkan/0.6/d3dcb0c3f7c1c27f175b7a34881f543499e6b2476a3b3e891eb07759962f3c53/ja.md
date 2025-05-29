VkPerformanceCounterKHRの高レベルラッパー。

拡張: VK*KHR*performance_query

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterKHR.html)

```julia
struct PerformanceCounterKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `unit::Vulkan.PerformanceCounterUnitKHR`
  * `scope::Vulkan.PerformanceCounterScopeKHR`
  * `storage::Vulkan.PerformanceCounterStorageKHR`
  * `uuid::NTuple{16, UInt8}`
