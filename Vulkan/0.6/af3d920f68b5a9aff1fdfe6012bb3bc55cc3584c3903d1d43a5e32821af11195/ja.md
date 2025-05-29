引数:

  * `pipeline_bind_point::PipelineBindPoint`
  * `input_attachments::Vector{_AttachmentReference}`
  * `color_attachments::Vector{_AttachmentReference}`
  * `preserve_attachments::Vector{UInt32}`
  * `flags::SubpassDescriptionFlag`: デフォルトは `0`
  * `resolve_attachments::Vector{_AttachmentReference}`: デフォルトは `C_NULL`
  * `depth_stencil_attachment::_AttachmentReference`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescription.html)

```julia
_SubpassDescription(
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    input_attachments::AbstractArray,
    color_attachments::AbstractArray,
    preserve_attachments::AbstractArray;
    flags,
    resolve_attachments,
    depth_stencil_attachment
) -> Vulkan._SubpassDescription

```
