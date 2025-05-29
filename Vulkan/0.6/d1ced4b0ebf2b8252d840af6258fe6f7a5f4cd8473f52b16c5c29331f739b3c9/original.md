Arguments:

  * `attachments::Vector{ImageView}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassAttachmentBeginInfo.html)

```julia
_RenderPassAttachmentBeginInfo(
    attachments::AbstractArray;
    next
) -> Vulkan._RenderPassAttachmentBeginInfo

```
