拡張: VK*KHR*video_queue

引数:

  * `coded_offset::_Offset2D`
  * `coded_extent::_Extent2D`
  * `base_array_layer::UInt32`
  * `image_view_binding::ImageView`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoPictureResourceInfoKHR.html)

```julia
_VideoPictureResourceInfoKHR(
    coded_offset::Vulkan._Offset2D,
    coded_extent::Vulkan._Extent2D,
    base_array_layer::Integer,
    image_view_binding;
    next
) -> Vulkan._VideoPictureResourceInfoKHR

```
