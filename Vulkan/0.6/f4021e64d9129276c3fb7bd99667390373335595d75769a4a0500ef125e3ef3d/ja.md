引数:

  * `render_area::_Rect2D`
  * `layer_count::UInt32`
  * `view_mask::UInt32`
  * `color_attachments::Vector{_RenderingAttachmentInfo}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::RenderingFlag`: デフォルトは `0`
  * `depth_attachment::_RenderingAttachmentInfo`: デフォルトは `C_NULL`
  * `stencil_attachment::_RenderingAttachmentInfo`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingInfo.html)

```julia
_RenderingInfo(
    render_area::Vulkan._Rect2D,
    layer_count::Integer,
    view_mask::Integer,
    color_attachments::AbstractArray;
    next,
    flags,
    depth_attachment,
    stencil_attachment
) -> Vulkan._RenderingInfo

```
