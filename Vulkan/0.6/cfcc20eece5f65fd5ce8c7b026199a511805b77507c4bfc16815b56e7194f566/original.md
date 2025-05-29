Extension: VK_EXT_descriptor_buffer

Arguments:

  * `address::UInt64`
  * `usage::BufferUsageFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorBufferBindingInfoEXT.html)

```julia
_DescriptorBufferBindingInfoEXT(
    address::Integer,
    usage::Vulkan.BufferUsageFlag;
    next
) -> Vulkan._DescriptorBufferBindingInfoEXT

```
