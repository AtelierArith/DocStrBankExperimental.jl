拡張: VK*EXT*descriptor_buffer

引数:

  * `type::DescriptorType`
  * `data::_DescriptorDataEXT`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorGetInfoEXT.html)

```julia
_DescriptorGetInfoEXT(
    type::Vulkan.DescriptorType,
    data::Vulkan._DescriptorDataEXT;
    next
) -> Vulkan._DescriptorGetInfoEXT

```
