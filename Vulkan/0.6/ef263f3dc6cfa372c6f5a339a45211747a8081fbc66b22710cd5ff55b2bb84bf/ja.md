拡張: VK*EXT*descriptor_buffer

引数:

  * `address::UInt64`
  * `usage::BufferUsageFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferBindingInfoEXT.html)

```julia
DescriptorBufferBindingInfoEXT(
    address::Integer,
    usage::Vulkan.BufferUsageFlag;
    next
) -> Vulkan.DescriptorBufferBindingInfoEXT

```
