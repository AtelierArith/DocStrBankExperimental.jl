High-level wrapper for VkQueueFamilyGlobalPriorityPropertiesKHR.

Extension: VK_KHR_global_priority

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyGlobalPriorityPropertiesKHR.html)

```julia
struct QueueFamilyGlobalPriorityPropertiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `priority_count::UInt32`
  * `priorities::NTuple{16, Vulkan.QueueGlobalPriorityKHR}`
