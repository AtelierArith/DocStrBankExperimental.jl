Arguments:

  * `src_buffer::Buffer`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{_BufferImageCopy2}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferToImageInfo2.html)

```julia
_CopyBufferToImageInfo2(
    src_buffer,
    dst_image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray;
    next
) -> Vulkan._CopyBufferToImageInfo2

```
