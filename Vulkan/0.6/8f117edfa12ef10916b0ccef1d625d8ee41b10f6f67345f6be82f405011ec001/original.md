Arguments:

  * `aspect_references::Vector{_InputAttachmentAspectReference}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassInputAttachmentAspectCreateInfo.html)

```julia
_RenderPassInputAttachmentAspectCreateInfo(
    aspect_references::AbstractArray;
    next
) -> Vulkan._RenderPassInputAttachmentAspectCreateInfo

```
