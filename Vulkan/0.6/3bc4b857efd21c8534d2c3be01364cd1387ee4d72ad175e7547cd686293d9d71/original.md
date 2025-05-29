High-level wrapper for VkDeviceFaultAddressInfoEXT.

Extension: VK_EXT_device_fault

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultAddressInfoEXT.html)

```julia
struct DeviceFaultAddressInfoEXT <: Vulkan.HighLevelStruct
```

  * `address_type::Vulkan.DeviceFaultAddressTypeEXT`
  * `reported_address::UInt64`
  * `address_precision::UInt64`
