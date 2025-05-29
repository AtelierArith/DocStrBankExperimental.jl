High-level wrapper for VkDeviceFaultCountsEXT.

Extension: VK_EXT_device_fault

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultCountsEXT.html)

```julia
struct DeviceFaultCountsEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `address_info_count::UInt32`
  * `vendor_info_count::UInt32`
  * `vendor_binary_size::UInt64`
