Extension: VK_EXT_fragment_density_map

Arguments:

  * `fragment_density_map_attachment::_AttachmentReference`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassFragmentDensityMapCreateInfoEXT.html)

```julia
_RenderPassFragmentDensityMapCreateInfoEXT(
    fragment_density_map_attachment::Vulkan._AttachmentReference;
    next
) -> Vulkan._RenderPassFragmentDensityMapCreateInfoEXT

```
