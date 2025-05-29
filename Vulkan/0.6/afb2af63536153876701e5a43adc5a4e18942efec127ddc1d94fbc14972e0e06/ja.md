拡張: VK*EXT*device*address*binding_report

引数:

  * `base_address::UInt64`
  * `size::UInt64`
  * `binding_type::DeviceAddressBindingTypeEXT`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DeviceAddressBindingFlagEXT`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceAddressBindingCallbackDataEXT.html)

```julia
DeviceAddressBindingCallbackDataEXT(
    base_address::Integer,
    size::Integer,
    binding_type::Vulkan.DeviceAddressBindingTypeEXT;
    next,
    flags
) -> Vulkan.DeviceAddressBindingCallbackDataEXT

```
