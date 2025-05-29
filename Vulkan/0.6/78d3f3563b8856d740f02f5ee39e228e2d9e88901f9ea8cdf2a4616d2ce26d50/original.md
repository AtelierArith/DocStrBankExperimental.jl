Arguments:

  * `attachments::Vector{ImageView}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassAttachmentBeginInfo.html)

```julia
RenderPassAttachmentBeginInfo(
    attachments::AbstractArray;
    next
) -> Vulkan.RenderPassAttachmentBeginInfo

```
