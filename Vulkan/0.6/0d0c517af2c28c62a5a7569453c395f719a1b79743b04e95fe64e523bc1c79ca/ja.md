拡張: VK*EXT*fragment*density*map

引数:

  * `fragment_density_map_attachment::_AttachmentReference`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassFragmentDensityMapCreateInfoEXT.html)

```julia
_RenderPassFragmentDensityMapCreateInfoEXT(
    fragment_density_map_attachment::Vulkan._AttachmentReference;
    next
) -> Vulkan._RenderPassFragmentDensityMapCreateInfoEXT

```
