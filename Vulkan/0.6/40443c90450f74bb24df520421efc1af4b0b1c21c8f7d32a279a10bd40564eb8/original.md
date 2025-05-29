Extension: VK_INTEL_performance_query

Arguments:

  * `performance_counters_sampling::QueryPoolSamplingModeINTEL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolPerformanceQueryCreateInfoINTEL.html)

```julia
_QueryPoolPerformanceQueryCreateInfoINTEL(
    performance_counters_sampling::Vulkan.QueryPoolSamplingModeINTEL;
    next
) -> Vulkan._QueryPoolPerformanceQueryCreateInfoINTEL

```
