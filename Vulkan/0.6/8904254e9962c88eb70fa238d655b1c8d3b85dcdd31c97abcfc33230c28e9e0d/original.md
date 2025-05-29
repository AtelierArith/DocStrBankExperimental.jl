Extension: VK_EXT_image_drm_format_modifier

Arguments:

  * `drm_format_modifier::UInt64`
  * `plane_layouts::Vector{_SubresourceLayout}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageDrmFormatModifierExplicitCreateInfoEXT.html)

```julia
_ImageDrmFormatModifierExplicitCreateInfoEXT(
    drm_format_modifier::Integer,
    plane_layouts::AbstractArray;
    next
) -> Vulkan._ImageDrmFormatModifierExplicitCreateInfoEXT

```
