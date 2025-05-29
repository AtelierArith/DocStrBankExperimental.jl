Extension: VK_EXT_device_fault

Arguments:

  * `description::String`
  * `vendor_fault_code::UInt64`
  * `vendor_fault_data::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceFaultVendorInfoEXT.html)

```julia
_DeviceFaultVendorInfoEXT(
    description::AbstractString,
    vendor_fault_code::Integer,
    vendor_fault_data::Integer
)

```
