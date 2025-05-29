High-level wrapper for VkDeviceDeviceMemoryReportCreateInfoEXT.

Extension: VK_EXT_device_memory_report

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceDeviceMemoryReportCreateInfoEXT.html)

```julia
struct DeviceDeviceMemoryReportCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `pfn_user_callback::Union{Ptr{Nothing}, Base.CFunction}`
  * `user_data::Ptr{Nothing}`
