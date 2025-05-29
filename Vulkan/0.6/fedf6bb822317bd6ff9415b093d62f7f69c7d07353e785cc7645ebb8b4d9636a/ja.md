拡張: VK*EXT*device_fault

引数:

  * `description::String`
  * `next::Any`: デフォルトは `C_NULL`
  * `address_infos::DeviceFaultAddressInfoEXT`: デフォルトは `C_NULL`
  * `vendor_infos::DeviceFaultVendorInfoEXT`: デフォルトは `C_NULL`
  * `vendor_binary_data::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultInfoEXT.html)

```julia
DeviceFaultInfoEXT(
    description::AbstractString;
    next,
    address_infos,
    vendor_infos,
    vendor_binary_data
) -> Vulkan.DeviceFaultInfoEXT

```
