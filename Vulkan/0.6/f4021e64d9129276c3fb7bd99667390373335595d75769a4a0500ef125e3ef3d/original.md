Arguments:

  * `render_area::_Rect2D`
  * `layer_count::UInt32`
  * `view_mask::UInt32`
  * `color_attachments::Vector{_RenderingAttachmentInfo}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::RenderingFlag`: defaults to `0`
  * `depth_attachment::_RenderingAttachmentInfo`: defaults to `C_NULL`
  * `stencil_attachment::_RenderingAttachmentInfo`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingInfo.html)

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
