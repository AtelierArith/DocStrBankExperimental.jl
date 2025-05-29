拡張: VK*EXT*image*drm*format_modifier

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `drm_format_modifier_properties::Vector{_DrmFormatModifierPropertiesEXT}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDrmFormatModifierPropertiesListEXT.html)

```julia
_DrmFormatModifierPropertiesListEXT(
;
    next,
    drm_format_modifier_properties
) -> Vulkan._DrmFormatModifierPropertiesListEXT

```
