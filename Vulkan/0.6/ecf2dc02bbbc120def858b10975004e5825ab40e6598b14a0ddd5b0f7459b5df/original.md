Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `src_buffer::Buffer`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{_BufferImageCopy}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyBufferToImage.html)

```julia
_cmd_copy_buffer_to_image(
    command_buffer,
    src_buffer,
    dst_image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray
)

```
