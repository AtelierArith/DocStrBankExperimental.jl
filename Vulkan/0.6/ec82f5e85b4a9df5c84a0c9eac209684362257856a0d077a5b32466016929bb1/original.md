Extension: VK_EXT_device_fault

Arguments:

  * `description::String`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `address_infos::_DeviceFaultAddressInfoEXT`: defaults to `C_NULL`
  * `vendor_infos::_DeviceFaultVendorInfoEXT`: defaults to `C_NULL`
  * `vendor_binary_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultInfoEXT.html)

```julia
_DeviceFaultInfoEXT(
    description::AbstractString;
    next,
    address_infos,
    vendor_infos,
    vendor_binary_data
)

```
