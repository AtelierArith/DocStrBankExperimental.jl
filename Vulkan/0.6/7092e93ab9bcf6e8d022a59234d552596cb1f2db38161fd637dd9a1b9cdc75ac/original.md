Arguments:

  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_buffer::Buffer`
  * `regions::Vector{_BufferImageCopy2}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageToBufferInfo2.html)

```julia
_CopyImageToBufferInfo2(
    src_image,
    src_image_layout::Vulkan.ImageLayout,
    dst_buffer,
    regions::AbstractArray;
    next
) -> Vulkan._CopyImageToBufferInfo2

```
