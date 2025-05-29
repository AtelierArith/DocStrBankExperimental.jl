引数:

  * `aspect_references::Vector{InputAttachmentAspectReference}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassInputAttachmentAspectCreateInfo.html)

```julia
RenderPassInputAttachmentAspectCreateInfo(
    aspect_references::AbstractArray;
    next
) -> Vulkan.RenderPassInputAttachmentAspectCreateInfo

```
