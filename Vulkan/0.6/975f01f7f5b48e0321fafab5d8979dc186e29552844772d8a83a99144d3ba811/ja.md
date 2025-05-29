引数:

  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{ImageCopy2}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageInfo2.html)

```julia
CopyImageInfo2(
    src_image::Vulkan.Image,
    src_image_layout::Vulkan.ImageLayout,
    dst_image::Vulkan.Image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray;
    next
) -> Vulkan.CopyImageInfo2

```
