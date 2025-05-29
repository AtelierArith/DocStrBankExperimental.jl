拡張機能: VK*NV*shading*rate*image

引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `image_layout::ImageLayout`
  * `image_view::ImageView`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdBindShadingRateImageNV.html)

```julia
cmd_bind_shading_rate_image_nv(
    command_buffer,
    image_layout::Vulkan.ImageLayout;
    image_view
)

```
