拡張: VK*EXT*descriptor_buffer

引数:

  * `address::UInt64`
  * `range::UInt64`
  * `format::Format`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorAddressInfoEXT.html)

```julia
DescriptorAddressInfoEXT(
    address::Integer,
    range::Integer,
    format::Vulkan.Format;
    next
) -> Vulkan.DescriptorAddressInfoEXT

```
