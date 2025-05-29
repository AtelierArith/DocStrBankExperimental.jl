Extension: VK_EXT_image_drm_format_modifier

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `image::Image`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageDrmFormatModifierPropertiesEXT.html)

```julia
_get_image_drm_format_modifier_properties_ext(
    device,
    image
) -> ResultTypes.Result{Vulkan._ImageDrmFormatModifierPropertiesEXT, Vulkan.VulkanError}

```
