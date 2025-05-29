VkPerformanceOverrideInfoINTELの高レベルラッパー。

拡張: VK*INTEL*performance_query

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPerformanceOverrideInfoINTEL.html)

```julia
struct PerformanceOverrideInfoINTEL <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::Vulkan.PerformanceOverrideTypeINTEL`
  * `enable::Bool`
  * `parameter::UInt64`
