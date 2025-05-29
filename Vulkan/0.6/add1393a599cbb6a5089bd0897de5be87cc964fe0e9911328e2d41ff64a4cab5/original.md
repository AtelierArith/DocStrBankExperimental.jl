Extension: VK_INTEL_performance_query

Arguments:

  * `marker::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceMarkerInfoINTEL.html)

```julia
_PerformanceMarkerInfoINTEL(
    marker::Integer;
    next
) -> Vulkan._PerformanceMarkerInfoINTEL

```
