拡張機能: VK*EXT*device_fault

引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `address_info_count::UInt32`: デフォルトは `0`
  * `vendor_info_count::UInt32`: デフォルトは `0`
  * `vendor_binary_size::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultCountsEXT.html)

```julia
DeviceFaultCountsEXT(
;
    next,
    address_info_count,
    vendor_info_count,
    vendor_binary_size
) -> Vulkan.DeviceFaultCountsEXT

```
