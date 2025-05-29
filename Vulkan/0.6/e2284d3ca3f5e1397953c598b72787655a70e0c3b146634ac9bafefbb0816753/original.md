Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `image::Image`
  * `image_layout::ImageLayout`
  * `color::_ClearColorValue`
  * `ranges::Vector{_ImageSubresourceRange}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdClearColorImage.html)

```julia
_cmd_clear_color_image(
    command_buffer,
    image,
    image_layout::Vulkan.ImageLayout,
    color::Vulkan._ClearColorValue,
    ranges::AbstractArray
)

```
