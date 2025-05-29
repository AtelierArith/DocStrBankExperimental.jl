拡張: VK*EXT*memory_budget

引数:

  * `heap_budget::NTuple{Int(VK_MAX_MEMORY_HEAPS), UInt64}`
  * `heap_usage::NTuple{Int(VK_MAX_MEMORY_HEAPS), UInt64}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryBudgetPropertiesEXT.html)

```julia
PhysicalDeviceMemoryBudgetPropertiesEXT(
    heap_budget::NTuple{16, UInt64},
    heap_usage::NTuple{16, UInt64};
    next
) -> Vulkan.PhysicalDeviceMemoryBudgetPropertiesEXT

```
