Extension: VK_EXT_image_drm_format_modifier

Arguments:

  * `drm_format_modifier::UInt64`
  * `sharing_mode::SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceImageDrmFormatModifierInfoEXT.html)

```julia
PhysicalDeviceImageDrmFormatModifierInfoEXT(
    drm_format_modifier::Integer,
    sharing_mode::Vulkan.SharingMode,
    queue_family_indices::AbstractArray;
    next
) -> Vulkan.PhysicalDeviceImageDrmFormatModifierInfoEXT

```
