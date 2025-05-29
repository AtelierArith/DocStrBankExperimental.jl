Extension: VK_EXT_descriptor_buffer

Arguments:

  * `address::UInt64`
  * `range::UInt64`
  * `format::Format`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorAddressInfoEXT.html)

```julia
DescriptorAddressInfoEXT(
    address::Integer,
    range::Integer,
    format::Vulkan.Format;
    next
) -> Vulkan.DescriptorAddressInfoEXT

```
