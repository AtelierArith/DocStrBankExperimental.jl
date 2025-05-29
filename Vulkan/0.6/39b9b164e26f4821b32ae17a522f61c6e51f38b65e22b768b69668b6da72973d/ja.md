VkDeviceAddressBindingCallbackDataEXTの高レベルラッパー。

拡張: VK*EXT*device*address*binding_report

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceAddressBindingCallbackDataEXT.html)

```julia
struct DeviceAddressBindingCallbackDataEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.DeviceAddressBindingFlagEXT`
  * `base_address::UInt64`
  * `size::UInt64`
  * `binding_type::Vulkan.DeviceAddressBindingTypeEXT`
