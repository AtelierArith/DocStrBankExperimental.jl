VkDeviceFaultInfoEXTの高レベルラッパー。

拡張: VK*EXT*device_fault

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultInfoEXT.html)

```julia
struct DeviceFaultInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `description::String`
  * `address_infos::Union{Ptr{Nothing}, Vulkan.DeviceFaultAddressInfoEXT}`
  * `vendor_infos::Union{Ptr{Nothing}, Vulkan.DeviceFaultVendorInfoEXT}`
  * `vendor_binary_data::Ptr{Nothing}`
