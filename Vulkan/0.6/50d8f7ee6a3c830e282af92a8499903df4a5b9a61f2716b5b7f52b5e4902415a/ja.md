拡張: VK*EXT*image*drm*format_modifier

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `image::Image`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetImageDrmFormatModifierPropertiesEXT.html)

```julia
get_image_drm_format_modifier_properties_ext(
    device,
    image
) -> ResultTypes.Result{Vulkan.ImageDrmFormatModifierPropertiesEXT, Vulkan.VulkanError}

```
