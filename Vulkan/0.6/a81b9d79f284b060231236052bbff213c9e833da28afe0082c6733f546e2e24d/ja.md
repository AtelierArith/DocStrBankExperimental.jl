拡張: VK*KHR*performance_query

引数:

  * `unit::PerformanceCounterUnitKHR`
  * `scope::PerformanceCounterScopeKHR`
  * `storage::PerformanceCounterStorageKHR`
  * `uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterKHR.html)

```julia
PerformanceCounterKHR(
    unit::Vulkan.PerformanceCounterUnitKHR,
    scope::Vulkan.PerformanceCounterScopeKHR,
    storage::Vulkan.PerformanceCounterStorageKHR,
    uuid::NTuple{16, UInt8};
    next
) -> Vulkan.PerformanceCounterKHR

```
