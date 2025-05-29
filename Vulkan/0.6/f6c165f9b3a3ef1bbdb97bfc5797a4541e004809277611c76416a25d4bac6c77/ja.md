引数:

  * `render_area::Rect2D`
  * `layer_count::UInt32`
  * `view_mask::UInt32`
  * `color_attachments::Vector{RenderingAttachmentInfo}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::RenderingFlag`: デフォルトは `0`
  * `depth_attachment::RenderingAttachmentInfo`: デフォルトは `C_NULL`
  * `stencil_attachment::RenderingAttachmentInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingInfo.html)

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
