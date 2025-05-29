Arguments:

  * `render_area::Rect2D`
  * `layer_count::UInt32`
  * `view_mask::UInt32`
  * `color_attachments::Vector{RenderingAttachmentInfo}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::RenderingFlag`: defaults to `0`
  * `depth_attachment::RenderingAttachmentInfo`: defaults to `C_NULL`
  * `stencil_attachment::RenderingAttachmentInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingInfo.html)

```julia
RenderingInfo(
    render_area::Vulkan.Rect2D,
    layer_count::Integer,
    view_mask::Integer,
    color_attachments::AbstractArray;
    next,
    flags,
    depth_attachment,
    stencil_attachment
) -> Vulkan.RenderingInfo

```
