Extension: VK_EXT_device_fault

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `address_info_count::UInt32`: defaults to `0`
  * `vendor_info_count::UInt32`: defaults to `0`
  * `vendor_binary_size::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultCountsEXT.html)

```julia
_DeviceFaultCountsEXT(
;
    next,
    address_info_count,
    vendor_info_count,
    vendor_binary_size
) -> Vulkan._DeviceFaultCountsEXT

```
