拡張: VK*EXT*image*drm*format_modifier

引数:

  * `drm_format_modifier::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageDrmFormatModifierPropertiesEXT.html)

```julia
_ImageDrmFormatModifierPropertiesEXT(
    drm_format_modifier::Integer;
    next
) -> Vulkan._ImageDrmFormatModifierPropertiesEXT

```
