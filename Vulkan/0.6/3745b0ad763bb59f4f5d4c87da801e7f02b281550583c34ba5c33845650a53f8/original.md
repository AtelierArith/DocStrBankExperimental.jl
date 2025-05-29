Extension: VK_KHR_video_queue

Arguments:

  * `format::Format`
  * `component_mapping::ComponentMapping`
  * `image_create_flags::ImageCreateFlag`
  * `image_type::ImageType`
  * `image_tiling::ImageTiling`
  * `image_usage_flags::ImageUsageFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoFormatPropertiesKHR.html)

```julia
VideoFormatPropertiesKHR(
    format::Vulkan.Format,
    component_mapping::Vulkan.ComponentMapping,
    image_create_flags::Vulkan.ImageCreateFlag,
    image_type::Vulkan.ImageType,
    image_tiling::Vulkan.ImageTiling,
    image_usage_flags::Vulkan.ImageUsageFlag;
    next
) -> Vulkan.VideoFormatPropertiesKHR

```
