Extension: VK_KHR_video_queue

Arguments:

  * `format::Format`
  * `component_mapping::_ComponentMapping`
  * `image_create_flags::ImageCreateFlag`
  * `image_type::ImageType`
  * `image_tiling::ImageTiling`
  * `image_usage_flags::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoFormatPropertiesKHR.html)

```julia
_VideoFormatPropertiesKHR(
    format::Vulkan.Format,
    component_mapping::Vulkan._ComponentMapping,
    image_create_flags::Vulkan.ImageCreateFlag,
    image_type::Vulkan.ImageType,
    image_tiling::Vulkan.ImageTiling,
    image_usage_flags::Vulkan.ImageUsageFlag;
    next
) -> Vulkan._VideoFormatPropertiesKHR

```
