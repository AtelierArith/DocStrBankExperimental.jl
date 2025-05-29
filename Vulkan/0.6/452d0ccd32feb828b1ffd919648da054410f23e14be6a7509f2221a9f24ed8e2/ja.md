引数:

  * `command_buffer::CommandBuffer` (externsync)
  * `src_image::Image`
  * `src_image_layout::ImageLayout`
  * `dst_image::Image`
  * `dst_image_layout::ImageLayout`
  * `regions::Vector{_ImageResolve}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCmdResolveImage.html)

```julia
_cmd_resolve_image(
    command_buffer,
    src_image,
    src_image_layout::Vulkan.ImageLayout,
    dst_image,
    dst_image_layout::Vulkan.ImageLayout,
    regions::AbstractArray
)

```
