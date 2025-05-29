拡張: VK*KHR*performance_query

引数:

  * `counter_pass_index::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceQuerySubmitInfoKHR.html)

```julia
_PerformanceQuerySubmitInfoKHR(
    counter_pass_index::Integer;
    next
) -> Vulkan._PerformanceQuerySubmitInfoKHR

```
