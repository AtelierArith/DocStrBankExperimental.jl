Extension: VK_EXT_device_fault

Arguments:

  * `address_type::DeviceFaultAddressTypeEXT`
  * `reported_address::UInt64`
  * `address_precision::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultAddressInfoEXT.html)

```julia
_DeviceFaultAddressInfoEXT(
    address_type::Vulkan.DeviceFaultAddressTypeEXT,
    reported_address::Integer,
    address_precision::Integer
) -> Vulkan._DeviceFaultAddressInfoEXT

```
