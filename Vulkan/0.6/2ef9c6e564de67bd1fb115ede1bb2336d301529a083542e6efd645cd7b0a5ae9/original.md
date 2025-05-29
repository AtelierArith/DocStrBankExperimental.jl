Extension: VK_EXT_hdr_metadata

Arguments:

  * `display_primary_red::_XYColorEXT`
  * `display_primary_green::_XYColorEXT`
  * `display_primary_blue::_XYColorEXT`
  * `white_point::_XYColorEXT`
  * `max_luminance::Float32`
  * `min_luminance::Float32`
  * `max_content_light_level::Float32`
  * `max_frame_average_light_level::Float32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkHdrMetadataEXT.html)

```julia
_HdrMetadataEXT(
    display_primary_red::Vulkan._XYColorEXT,
    display_primary_green::Vulkan._XYColorEXT,
    display_primary_blue::Vulkan._XYColorEXT,
    white_point::Vulkan._XYColorEXT,
    max_luminance::Real,
    min_luminance::Real,
    max_content_light_level::Real,
    max_frame_average_light_level::Real;
    next
) -> Vulkan._HdrMetadataEXT

```
