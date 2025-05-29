拡張: VK*EXT*hdr_metadata

引数:

  * `display_primary_red::XYColorEXT`
  * `display_primary_green::XYColorEXT`
  * `display_primary_blue::XYColorEXT`
  * `white_point::XYColorEXT`
  * `max_luminance::Float32`
  * `min_luminance::Float32`
  * `max_content_light_level::Float32`
  * `max_frame_average_light_level::Float32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkHdrMetadataEXT.html)

```julia
HdrMetadataEXT(
    display_primary_red::Vulkan.XYColorEXT,
    display_primary_green::Vulkan.XYColorEXT,
    display_primary_blue::Vulkan.XYColorEXT,
    white_point::Vulkan.XYColorEXT,
    max_luminance::Real,
    min_luminance::Real,
    max_content_light_level::Real,
    max_frame_average_light_level::Real;
    next
) -> Vulkan.HdrMetadataEXT

```
