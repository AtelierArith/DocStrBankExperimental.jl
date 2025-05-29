拡張: VK*EXT*image*drm*format_modifier

引数:

  * `drm_format_modifier::UInt64`
  * `plane_layouts::Vector{_SubresourceLayout}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageDrmFormatModifierExplicitCreateInfoEXT.html)

```julia
_ImageDrmFormatModifierExplicitCreateInfoEXT(
    drm_format_modifier::Integer,
    plane_layouts::AbstractArray;
    next
) -> Vulkan._ImageDrmFormatModifierExplicitCreateInfoEXT

```
