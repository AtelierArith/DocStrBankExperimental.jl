Extension: VK_KHR_global_priority

Arguments:

  * `global_priority::QueueGlobalPriorityKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceQueueGlobalPriorityCreateInfoKHR.html)

```julia
_DeviceQueueGlobalPriorityCreateInfoKHR(
    global_priority::Vulkan.QueueGlobalPriorityKHR;
    next
) -> Vulkan._DeviceQueueGlobalPriorityCreateInfoKHR

```
