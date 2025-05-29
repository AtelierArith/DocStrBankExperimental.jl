Arguments:

  * `attachments::Vector{AttachmentDescription2}`
  * `subpasses::Vector{SubpassDescription2}`
  * `dependencies::Vector{SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo2.html)

```julia
RenderPassCreateInfo2(
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray,
    correlated_view_masks::AbstractArray;
    next,
    flags
) -> Vulkan.RenderPassCreateInfo2

```
