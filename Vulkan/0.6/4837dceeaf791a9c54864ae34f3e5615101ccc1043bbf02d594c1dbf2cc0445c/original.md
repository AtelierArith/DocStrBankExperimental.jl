Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `image::Image`
  * `image_layout::ImageLayout`
  * `color::ClearColorValue`
  * `ranges::Vector{ImageSubresourceRange}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdClearColorImage.html)

```julia
cmd_clear_color_image(
    command_buffer,
    image,
    image_layout::Vulkan.ImageLayout,
    color::Vulkan.ClearColorValue,
    ranges::AbstractArray
)

```
