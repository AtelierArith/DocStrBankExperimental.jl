拡張: VK*KHR*global_priority

引数:

  * `global_priority_query::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceGlobalPriorityQueryFeaturesKHR.html)

```julia
_PhysicalDeviceGlobalPriorityQueryFeaturesKHR(
    global_priority_query::Bool;
    next
) -> Vulkan._PhysicalDeviceGlobalPriorityQueryFeaturesKHR

```
