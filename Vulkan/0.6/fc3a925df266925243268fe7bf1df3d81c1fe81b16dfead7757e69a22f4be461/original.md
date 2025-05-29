Arguments:

  * `aspect_references::Vector{InputAttachmentAspectReference}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassInputAttachmentAspectCreateInfo.html)

```julia
RenderPassInputAttachmentAspectCreateInfo(
    aspect_references::AbstractArray;
    next
) -> Vulkan.RenderPassInputAttachmentAspectCreateInfo

```
