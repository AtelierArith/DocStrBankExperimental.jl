Extension: VK_KHR_performance_query

Arguments:

  * `counter_pass_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceQuerySubmitInfoKHR.html)

```julia
_PerformanceQuerySubmitInfoKHR(
    counter_pass_index::Integer;
    next
) -> Vulkan._PerformanceQuerySubmitInfoKHR

```
