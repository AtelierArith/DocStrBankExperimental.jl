Extension: VK_EXT_image_drm_format_modifier

Arguments:

  * `drm_format_modifier::UInt64`
  * `drm_format_modifier_plane_count::UInt32`
  * `drm_format_modifier_tiling_features::FormatFeatureFlag`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDrmFormatModifierPropertiesEXT.html)

```julia
_DrmFormatModifierPropertiesEXT(
    drm_format_modifier::Integer,
    drm_format_modifier_plane_count::Integer,
    drm_format_modifier_tiling_features::Vulkan.FormatFeatureFlag
) -> Vulkan._DrmFormatModifierPropertiesEXT

```
