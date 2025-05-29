拡張: VK*INTEL*performance_query

引数:

  * `type::PerformanceOverrideTypeINTEL`
  * `enable::Bool`
  * `parameter::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceOverrideInfoINTEL.html)

```julia
_PerformanceOverrideInfoINTEL(
    type::Vulkan.PerformanceOverrideTypeINTEL,
    enable::Bool,
    parameter::Integer;
    next
) -> Vulkan._PerformanceOverrideInfoINTEL

```
