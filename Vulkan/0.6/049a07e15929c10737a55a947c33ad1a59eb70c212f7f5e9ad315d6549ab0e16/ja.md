拡張: VK*KHR*performance_query

引数:

  * `queue_family_index::UInt32`
  * `counter_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolPerformanceCreateInfoKHR.html)

```julia
_QueryPoolPerformanceCreateInfoKHR(
    queue_family_index::Integer,
    counter_indices::AbstractArray;
    next
) -> Vulkan._QueryPoolPerformanceCreateInfoKHR

```
