引数:

  * `attachments::Vector{ImageView}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassAttachmentBeginInfo.html)

```julia
_RenderPassAttachmentBeginInfo(
    attachments::AbstractArray;
    next
) -> Vulkan._RenderPassAttachmentBeginInfo

```
