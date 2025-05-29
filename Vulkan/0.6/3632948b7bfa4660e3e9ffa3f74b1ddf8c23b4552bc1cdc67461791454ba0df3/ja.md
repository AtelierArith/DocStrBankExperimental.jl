拡張: VK*KHR*global_priority

引数:

  * `global_priority::QueueGlobalPriorityKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueGlobalPriorityCreateInfoKHR.html)

```julia
_DeviceQueueGlobalPriorityCreateInfoKHR(
    global_priority::Vulkan.QueueGlobalPriorityKHR;
    next
) -> Vulkan._DeviceQueueGlobalPriorityCreateInfoKHR

```
