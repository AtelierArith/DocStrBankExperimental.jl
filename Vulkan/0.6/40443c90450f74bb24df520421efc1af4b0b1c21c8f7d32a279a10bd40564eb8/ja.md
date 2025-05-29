拡張: VK*INTEL*performance_query

引数:

  * `performance_counters_sampling::QueryPoolSamplingModeINTEL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolPerformanceQueryCreateInfoINTEL.html)

```julia
_QueryPoolPerformanceQueryCreateInfoINTEL(
    performance_counters_sampling::Vulkan.QueryPoolSamplingModeINTEL;
    next
) -> Vulkan._QueryPoolPerformanceQueryCreateInfoINTEL

```
