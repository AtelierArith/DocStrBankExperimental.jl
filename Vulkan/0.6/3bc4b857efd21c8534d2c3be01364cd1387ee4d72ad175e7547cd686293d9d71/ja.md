VkDeviceFaultAddressInfoEXTの高レベルラッパー。

拡張: VK*EXT*device_fault

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultAddressInfoEXT.html)

```julia
struct DeviceFaultAddressInfoEXT <: Vulkan.HighLevelStruct
```

  * `address_type::Vulkan.DeviceFaultAddressTypeEXT`
  * `reported_address::UInt64`
  * `address_precision::UInt64`
