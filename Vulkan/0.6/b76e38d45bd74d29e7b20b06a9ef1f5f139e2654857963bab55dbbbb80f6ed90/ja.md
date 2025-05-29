拡張: VK*EXT*mutable*descriptor*type

引数:

  * `mutable_descriptor_type_lists::Vector{MutableDescriptorTypeListEXT}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMutableDescriptorTypeCreateInfoEXT.html)

```julia
MutableDescriptorTypeCreateInfoEXT(
    mutable_descriptor_type_lists::AbstractArray;
    next
) -> Vulkan.MutableDescriptorTypeCreateInfoEXT

```
