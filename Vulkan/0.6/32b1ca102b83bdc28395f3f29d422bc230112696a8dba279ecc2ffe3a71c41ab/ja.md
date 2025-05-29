引数:

  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_buffer::Buffer`
  * `regions::Vector{BufferImageCopy2}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageToBufferInfo2.html)

```julia
CopyImageToBufferInfo2(
    src_image::Vulkan.Image,
    src_image_layout::Vulkan.ImageLayout,
    dst_buffer::Vulkan.Buffer,
    regions::AbstractArray;
    next
) -> Vulkan.CopyImageToBufferInfo2

```
