VkDeviceFaultVendorInfoEXTの高レベルラッパー。

拡張: VK*EXT*device_fault

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultVendorInfoEXT.html)

```julia
struct DeviceFaultVendorInfoEXT <: Vulkan.HighLevelStruct
```

  * `description::String`
  * `vendor_fault_code::UInt64`
  * `vendor_fault_data::UInt64`
