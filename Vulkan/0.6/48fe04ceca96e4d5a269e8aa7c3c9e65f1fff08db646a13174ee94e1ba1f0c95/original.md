Extension: VK_EXT_descriptor_buffer

Arguments:

  * `type::DescriptorType`
  * `data::_DescriptorDataEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorGetInfoEXT.html)

```julia
_DescriptorGetInfoEXT(
    type::Vulkan.DescriptorType,
    data::Vulkan._DescriptorDataEXT;
    next
) -> Vulkan._DescriptorGetInfoEXT

```
