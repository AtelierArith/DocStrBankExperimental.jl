Extension: VK_KHR_video_queue

Arguments:

  * `coded_offset::_Offset2D`
  * `coded_extent::_Extent2D`
  * `base_array_layer::UInt32`
  * `image_view_binding::ImageView`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoPictureResourceInfoKHR.html)

```julia
_VideoPictureResourceInfoKHR(
    coded_offset::Vulkan._Offset2D,
    coded_extent::Vulkan._Extent2D,
    base_array_layer::Integer,
    image_view_binding;
    next
) -> Vulkan._VideoPictureResourceInfoKHR

```
