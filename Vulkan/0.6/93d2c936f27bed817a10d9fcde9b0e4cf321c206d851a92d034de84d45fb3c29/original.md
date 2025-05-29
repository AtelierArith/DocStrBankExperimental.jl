Extension: VK_NV_shading_rate_image

Arguments:

  * `command_buffer::CommandBuffer` (externsync)
  * `image_layout::ImageLayout`
  * `image_view::ImageView`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindShadingRateImageNV.html)

```julia
_cmd_bind_shading_rate_image_nv(
    command_buffer,
    image_layout::Vulkan.ImageLayout;
    image_view
)

```
