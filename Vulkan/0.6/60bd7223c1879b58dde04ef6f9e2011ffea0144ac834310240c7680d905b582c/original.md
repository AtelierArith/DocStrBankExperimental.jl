Extension: VK_KHR_performance_query

Arguments:

  * `queue_family_index::UInt32`
  * `counter_indices::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolPerformanceCreateInfoKHR.html)

```julia
QueryPoolPerformanceCreateInfoKHR(
    queue_family_index::Integer,
    counter_indices::AbstractArray;
    next
) -> Vulkan.QueryPoolPerformanceCreateInfoKHR

```
