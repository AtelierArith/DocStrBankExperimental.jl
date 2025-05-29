Extension: VK_KHR_performance_query

Arguments:

  * `unit::PerformanceCounterUnitKHR`
  * `scope::PerformanceCounterScopeKHR`
  * `storage::PerformanceCounterStorageKHR`
  * `uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceCounterKHR.html)

```julia
_PerformanceCounterKHR(
    unit::Vulkan.PerformanceCounterUnitKHR,
    scope::Vulkan.PerformanceCounterScopeKHR,
    storage::Vulkan.PerformanceCounterStorageKHR,
    uuid::NTuple{16, UInt8};
    next
) -> Vulkan._PerformanceCounterKHR

```
