Extension: VK_EXT_image_drm_format_modifier

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `drm_format_modifier_properties::Vector{_DrmFormatModifierProperties2EXT}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDrmFormatModifierPropertiesList2EXT.html)

```julia
_DrmFormatModifierPropertiesList2EXT(
;
    next,
    drm_format_modifier_properties
) -> Vulkan._DrmFormatModifierPropertiesList2EXT

```
