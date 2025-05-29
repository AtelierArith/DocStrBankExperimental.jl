Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_buffer::Buffer`
  * `regions::Vector{BufferImageCopy}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyImageToBuffer.html)

```julia
cmd_copy_image_to_buffer(
    command_buffer,
    src_image,
    src_image_layout::Vulkan.ImageLayout,
    dst_buffer,
    regions::AbstractArray
)

```
