拡張: VK*KHR*performance_query

引数:

  * `allow_command_buffer_query_copies::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePerformanceQueryPropertiesKHR.html)

```julia
_PhysicalDevicePerformanceQueryPropertiesKHR(
    allow_command_buffer_query_copies::Bool;
    next
) -> Vulkan._PhysicalDevicePerformanceQueryPropertiesKHR

```
