Extension: VK_KHR_performance_query

Arguments:

  * `allow_command_buffer_query_copies::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePerformanceQueryPropertiesKHR.html)

```julia
_PhysicalDevicePerformanceQueryPropertiesKHR(
    allow_command_buffer_query_copies::Bool;
    next
) -> Vulkan._PhysicalDevicePerformanceQueryPropertiesKHR

```
