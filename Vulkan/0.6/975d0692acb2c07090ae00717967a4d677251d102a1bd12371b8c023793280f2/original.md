Extension: VK_EXT_device_memory_report

Arguments:

  * `device_memory_report::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDeviceMemoryReportFeaturesEXT.html)

```julia
_PhysicalDeviceDeviceMemoryReportFeaturesEXT(
    device_memory_report::Bool;
    next
) -> Vulkan._PhysicalDeviceDeviceMemoryReportFeaturesEXT

```
