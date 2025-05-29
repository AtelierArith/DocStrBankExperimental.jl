Extension: VK_EXT_mutable_descriptor_type

Arguments:

  * `mutable_descriptor_type_lists::Vector{_MutableDescriptorTypeListEXT}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMutableDescriptorTypeCreateInfoEXT.html)

```julia
_MutableDescriptorTypeCreateInfoEXT(
    mutable_descriptor_type_lists::AbstractArray;
    next
) -> Vulkan._MutableDescriptorTypeCreateInfoEXT

```
