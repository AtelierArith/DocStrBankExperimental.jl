Extension: VK_EXT_memory_budget

Arguments:

  * `heap_budget::NTuple{Int(VK_MAX_MEMORY_HEAPS), UInt64}`
  * `heap_usage::NTuple{Int(VK_MAX_MEMORY_HEAPS), UInt64}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryBudgetPropertiesEXT.html)

```julia
PhysicalDeviceMemoryBudgetPropertiesEXT(
    heap_budget::NTuple{16, UInt64},
    heap_usage::NTuple{16, UInt64};
    next
) -> Vulkan.PhysicalDeviceMemoryBudgetPropertiesEXT

```
