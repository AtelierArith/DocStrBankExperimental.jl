Arguments:

  * `src_buffer::Buffer`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{BufferImageCopy2}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferToImageInfo2.html)

```julia
CopyBufferToImageInfo2(
    src_buffer::Vulkan.Buffer,
    dst_image::Vulkan.Image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray;
    next
) -> Vulkan.CopyBufferToImageInfo2

```
