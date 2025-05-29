拡張: VK*EXT*image*drm*format_modifier

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `drm_format_modifier_properties::Vector{_DrmFormatModifierProperties2EXT}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDrmFormatModifierPropertiesList2EXT.html)

```julia
_DrmFormatModifierPropertiesList2EXT(
;
    next,
    drm_format_modifier_properties
) -> Vulkan._DrmFormatModifierPropertiesList2EXT

```
