Extension: VK_EXT_image_drm_format_modifier

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `drm_format_modifier_properties::Vector{_DrmFormatModifierPropertiesEXT}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDrmFormatModifierPropertiesListEXT.html)

```julia
_DrmFormatModifierPropertiesListEXT(
;
    next,
    drm_format_modifier_properties
) -> Vulkan._DrmFormatModifierPropertiesListEXT

```
