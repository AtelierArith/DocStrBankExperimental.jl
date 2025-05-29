High-level wrapper for VkPhysicalDeviceMemoryBudgetPropertiesEXT.

Extension: VK_EXT_memory_budget

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryBudgetPropertiesEXT.html)

```julia
struct PhysicalDeviceMemoryBudgetPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `heap_budget::NTuple{16, UInt64}`
  * `heap_usage::NTuple{16, UInt64}`
