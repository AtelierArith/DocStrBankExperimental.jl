Extension: VK_EXT_device_memory_report

Arguments:

  * `flags::UInt32`
  * `pfn_user_callback::FunctionPtr`
  * `user_data::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceDeviceMemoryReportCreateInfoEXT.html)

```julia
DeviceDeviceMemoryReportCreateInfoEXT(
    flags::Integer,
    pfn_user_callback::Union{Ptr{Nothing}, Base.CFunction},
    user_data::Ptr{Nothing};
    next
) -> Vulkan.DeviceDeviceMemoryReportCreateInfoEXT

```
