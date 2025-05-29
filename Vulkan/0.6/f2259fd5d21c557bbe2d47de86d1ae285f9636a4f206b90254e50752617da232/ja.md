拡張: VK*EXT*image*drm*format_modifier

引数:

  * `drm_format_modifier::UInt64`
  * `plane_layouts::Vector{SubresourceLayout}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageDrmFormatModifierExplicitCreateInfoEXT.html)

```julia
ImageDrmFormatModifierExplicitCreateInfoEXT(
    drm_format_modifier::Integer,
    plane_layouts::AbstractArray;
    next
) -> Vulkan.ImageDrmFormatModifierExplicitCreateInfoEXT

```
