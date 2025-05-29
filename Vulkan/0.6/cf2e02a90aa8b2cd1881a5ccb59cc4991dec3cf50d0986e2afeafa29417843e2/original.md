Extension: VK_KHR_performance_query

Arguments:

  * `performance_counter_query_pools::Bool`
  * `performance_counter_multiple_query_pools::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePerformanceQueryFeaturesKHR.html)

```julia
_PhysicalDevicePerformanceQueryFeaturesKHR(
    performance_counter_query_pools::Bool,
    performance_counter_multiple_query_pools::Bool;
    next
) -> Vulkan._PhysicalDevicePerformanceQueryFeaturesKHR

```
