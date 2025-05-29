Arguments:

  * `attachments::Vector{AttachmentDescription}`
  * `subpasses::Vector{SubpassDescription}`
  * `dependencies::Vector{SubpassDependency}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo.html)

```julia
RenderPassCreateInfo(
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray;
    next,
    flags
) -> Vulkan.RenderPassCreateInfo

```
