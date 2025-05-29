引数:

  * `attachments::Vector{_AttachmentDescription2}`
  * `subpasses::Vector{_SubpassDescription2}`
  * `dependencies::Vector{_SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::RenderPassCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo2.html)

```julia
_RenderPassCreateInfo2(
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray,
    correlated_view_masks::AbstractArray;
    next,
    flags
) -> Vulkan._RenderPassCreateInfo2

```
