VkQueueFamilyGlobalPriorityPropertiesKHRの高レベルラッパー。

拡張: VK*KHR*global_priority

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyGlobalPriorityPropertiesKHR.html)

```julia
struct QueueFamilyGlobalPriorityPropertiesKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `priority_count::UInt32`
  * `priorities::NTuple{16, Vulkan.QueueGlobalPriorityKHR}`
