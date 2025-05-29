Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `image::Image`
  * `image_layout::ImageLayout`
  * `depth_stencil::_ClearDepthStencilValue`
  * `ranges::Vector{_ImageSubresourceRange}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdClearDepthStencilImage.html)

```julia
_cmd_clear_depth_stencil_image(
    command_buffer,
    image,
    image_layout::Vulkan.ImageLayout,
    depth_stencil::Vulkan._ClearDepthStencilValue,
    ranges::AbstractArray
)

```
