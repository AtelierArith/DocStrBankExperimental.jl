引数:

  * `aspect_references::Vector{_InputAttachmentAspectReference}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassInputAttachmentAspectCreateInfo.html)

```julia
_RenderPassInputAttachmentAspectCreateInfo(
    aspect_references::AbstractArray;
    next
) -> Vulkan._RenderPassInputAttachmentAspectCreateInfo

```
