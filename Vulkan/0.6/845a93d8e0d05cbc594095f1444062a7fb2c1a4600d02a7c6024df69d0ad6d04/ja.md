VkPhysicalDeviceMemoryBudgetPropertiesEXTの高レベルラッパー。

拡張: VK*EXT*memory_budget

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryBudgetPropertiesEXT.html)

```julia
struct PhysicalDeviceMemoryBudgetPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `heap_budget::NTuple{16, UInt64}`
  * `heap_usage::NTuple{16, UInt64}`
