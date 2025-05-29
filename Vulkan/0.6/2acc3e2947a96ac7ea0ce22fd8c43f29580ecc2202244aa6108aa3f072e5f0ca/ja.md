拡張: VK*KHR*performance_query

引数:

  * `performance_counter_query_pools::Bool`
  * `performance_counter_multiple_query_pools::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePerformanceQueryFeaturesKHR.html)

```julia
PhysicalDevicePerformanceQueryFeaturesKHR(
    performance_counter_query_pools::Bool,
    performance_counter_multiple_query_pools::Bool;
    next
) -> Vulkan.PhysicalDevicePerformanceQueryFeaturesKHR

```
