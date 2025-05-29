拡張: VK*EXT*device*memory*report

引数:

  * `device_memory_report::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDeviceMemoryReportFeaturesEXT.html)

```julia
_PhysicalDeviceDeviceMemoryReportFeaturesEXT(
    device_memory_report::Bool;
    next
) -> Vulkan._PhysicalDeviceDeviceMemoryReportFeaturesEXT

```
