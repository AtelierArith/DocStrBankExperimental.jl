Extension: VK_INTEL_performance_query

Arguments:

  * `type::PerformanceOverrideTypeINTEL`
  * `enable::Bool`
  * `parameter::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceOverrideInfoINTEL.html)

```julia
PerformanceOverrideInfoINTEL(
    type::Vulkan.PerformanceOverrideTypeINTEL,
    enable::Bool,
    parameter::Integer;
    next
) -> Vulkan.PerformanceOverrideInfoINTEL

```
