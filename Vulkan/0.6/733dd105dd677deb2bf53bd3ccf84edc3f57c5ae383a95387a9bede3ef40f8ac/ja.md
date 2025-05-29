拡張: VK*NV*copy*memory*indirect

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `copy_buffer_address::UInt64`
  * `stride::UInt32`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `image_subresources::Vector{_ImageSubresourceLayers}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdCopyMemoryToImageIndirectNV.html)

```julia
_cmd_copy_memory_to_image_indirect_nv(
    command_buffer,
    copy_buffer_address::Integer,
    stride::Integer,
    dst_image,
    dst_image_layout::Vulkan.ImageLayout,
    image_subresources::AbstractArray
)

```
