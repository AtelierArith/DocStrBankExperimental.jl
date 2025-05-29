Extension: VK_EXT_device_address_binding_report

Arguments:

  * `base_address::UInt64`
  * `size::UInt64`
  * `binding_type::DeviceAddressBindingTypeEXT`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DeviceAddressBindingFlagEXT`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceAddressBindingCallbackDataEXT.html)

```julia
DeviceAddressBindingCallbackDataEXT(
    base_address::Integer,
    size::Integer,
    binding_type::Vulkan.DeviceAddressBindingTypeEXT;
    next,
    flags
) -> Vulkan.DeviceAddressBindingCallbackDataEXT

```
