引数:

  * `attachments::Vector{_AttachmentDescription}`
  * `subpasses::Vector{_SubpassDescription}`
  * `dependencies::Vector{_SubpassDependency}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::RenderPassCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo.html)

```julia
_RenderPassCreateInfo(
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray;
    next,
    flags
) -> Vulkan._RenderPassCreateInfo

```
