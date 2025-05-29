拡張: VK*EXT*descriptor_buffer

引数:

  * `type::DescriptorType`
  * `data::DescriptorDataEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorGetInfoEXT.html)

```julia
DescriptorGetInfoEXT(
    type::Vulkan.DescriptorType,
    data::Vulkan.DescriptorDataEXT;
    next
) -> Vulkan.DescriptorGetInfoEXT

```
