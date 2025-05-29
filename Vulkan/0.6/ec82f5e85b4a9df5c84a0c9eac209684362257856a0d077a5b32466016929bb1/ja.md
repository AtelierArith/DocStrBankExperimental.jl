拡張機能: VK*EXT*device_fault

引数:

  * `description::String`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `address_infos::_DeviceFaultAddressInfoEXT`: デフォルトは `C_NULL`
  * `vendor_infos::_DeviceFaultVendorInfoEXT`: デフォルトは `C_NULL`
  * `vendor_binary_data::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultInfoEXT.html)

```julia
_DeviceFaultInfoEXT(
    description::AbstractString;
    next,
    address_infos,
    vendor_infos,
    vendor_binary_data
)

```
