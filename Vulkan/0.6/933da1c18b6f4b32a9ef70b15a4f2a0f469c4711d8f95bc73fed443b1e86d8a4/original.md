Arguments:

  * `attachments::Vector{_AttachmentDescription}`
  * `subpasses::Vector{_SubpassDescription}`
  * `dependencies::Vector{_SubpassDependency}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo.html)

```julia
_RenderPassCreateInfo(
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray;
    next,
    flags
) -> Vulkan._RenderPassCreateInfo

```
