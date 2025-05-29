Extension: VK_INTEL_performance_query

Arguments:

  * `marker::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceStreamMarkerInfoINTEL.html)

```julia
_PerformanceStreamMarkerInfoINTEL(
    marker::Integer;
    next
) -> Vulkan._PerformanceStreamMarkerInfoINTEL

```
