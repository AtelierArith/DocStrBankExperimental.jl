引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `image::Image`
  * `image_layout::ImageLayout`
  * `depth_stencil::ClearDepthStencilValue`
  * `ranges::Vector{ImageSubresourceRange}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdClearDepthStencilImage.html)

```julia
cmd_clear_depth_stencil_image(
    command_buffer,
    image,
    image_layout::Vulkan.ImageLayout,
    depth_stencil::Vulkan.ClearDepthStencilValue,
    ranges::AbstractArray
)

```
