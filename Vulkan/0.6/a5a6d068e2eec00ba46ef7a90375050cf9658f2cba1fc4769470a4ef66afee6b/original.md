Extension: VK_KHR_video_queue

Arguments:

  * `coded_offset::Offset2D`
  * `coded_extent::Extent2D`
  * `base_array_layer::UInt32`
  * `image_view_binding::ImageView`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoPictureResourceInfoKHR.html)

```julia
VideoPictureResourceInfoKHR(
    coded_offset::Vulkan.Offset2D,
    coded_extent::Vulkan.Extent2D,
    base_array_layer::Integer,
    image_view_binding::Vulkan.ImageView;
    next
) -> Vulkan.VideoPictureResourceInfoKHR

```
