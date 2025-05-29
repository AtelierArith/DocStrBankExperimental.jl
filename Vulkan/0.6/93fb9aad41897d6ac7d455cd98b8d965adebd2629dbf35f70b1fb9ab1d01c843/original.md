High-level wrapper for VkDeviceFaultInfoEXT.

Extension: VK_EXT_device_fault

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultInfoEXT.html)

```julia
struct DeviceFaultInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `description::String`
  * `address_infos::Union{Ptr{Nothing}, Vulkan.DeviceFaultAddressInfoEXT}`
  * `vendor_infos::Union{Ptr{Nothing}, Vulkan.DeviceFaultVendorInfoEXT}`
  * `vendor_binary_data::Ptr{Nothing}`
