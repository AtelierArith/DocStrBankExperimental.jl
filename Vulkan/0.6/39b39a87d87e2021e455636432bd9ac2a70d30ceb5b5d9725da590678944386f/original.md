Extension: VK_EXT_descriptor_buffer

Arguments:

  * `type::DescriptorType`
  * `data::DescriptorDataEXT`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorGetInfoEXT.html)

```julia
DescriptorGetInfoEXT(
    type::Vulkan.DescriptorType,
    data::Vulkan.DescriptorDataEXT;
    next
) -> Vulkan.DescriptorGetInfoEXT

```
