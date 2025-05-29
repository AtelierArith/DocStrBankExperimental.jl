Extension: VK_EXT_device_fault

Arguments:

  * `description::String`
  * `next::Any`: defaults to `C_NULL`
  * `address_infos::DeviceFaultAddressInfoEXT`: defaults to `C_NULL`
  * `vendor_infos::DeviceFaultVendorInfoEXT`: defaults to `C_NULL`
  * `vendor_binary_data::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultInfoEXT.html)

```julia
DeviceFaultInfoEXT(
    description::AbstractString;
    next,
    address_infos,
    vendor_infos,
    vendor_binary_data
) -> Vulkan.DeviceFaultInfoEXT

```
