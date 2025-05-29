拡張: VK*KHR*global_priority

引数:

  * `priority_count::UInt32`
  * `priorities::NTuple{Int(VK_MAX_GLOBAL_PRIORITY_SIZE_KHR), QueueGlobalPriorityKHR}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyGlobalPriorityPropertiesKHR.html)

```julia
QueueFamilyGlobalPriorityPropertiesKHR(
    priority_count::Integer,
    priorities::NTuple{16, Vulkan.QueueGlobalPriorityKHR};
    next
) -> Vulkan.QueueFamilyGlobalPriorityPropertiesKHR

```
