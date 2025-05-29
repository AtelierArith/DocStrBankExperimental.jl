拡張: VK*INTEL*performance_query

引数:

  * `marker::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceMarkerInfoINTEL.html)

```julia
_PerformanceMarkerInfoINTEL(
    marker::Integer;
    next
) -> Vulkan._PerformanceMarkerInfoINTEL

```
