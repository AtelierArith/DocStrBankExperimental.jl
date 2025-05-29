引数:

  * `attachments::Vector{ImageView}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassAttachmentBeginInfo.html)

```julia
RenderPassAttachmentBeginInfo(
    attachments::AbstractArray;
    next
) -> Vulkan.RenderPassAttachmentBeginInfo

```
