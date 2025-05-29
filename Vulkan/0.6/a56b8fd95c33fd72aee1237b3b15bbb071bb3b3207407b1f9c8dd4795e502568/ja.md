引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `view_mask::UInt32`
  * `input_attachments::Vector{AttachmentReference2}`
  * `color_attachments::Vector{AttachmentReference2}`
  * `preserve_attachments::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::SubpassDescriptionFlag`: デフォルトは `0`
  * `resolve_attachments::Vector{AttachmentReference2}`: デフォルトは `C_NULL`
  * `depth_stencil_attachment::AttachmentReference2`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescription2.html)

```julia
SubpassDescription2(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    view_mask::Integer,
    input_attachments::AbstractArray,
    color_attachments::AbstractArray,
    preserve_attachments::AbstractArray;
    next,
    flags,
    resolve_attachments,
    depth_stencil_attachment
) -> Vulkan.SubpassDescription2

```
