引数:

  * `attachments::Vector{AttachmentDescription}`
  * `subpasses::Vector{SubpassDescription}`
  * `dependencies::Vector{SubpassDependency}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::RenderPassCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo.html)

```julia
RenderPassCreateInfo(
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray;
    next,
    flags
) -> Vulkan.RenderPassCreateInfo

```
