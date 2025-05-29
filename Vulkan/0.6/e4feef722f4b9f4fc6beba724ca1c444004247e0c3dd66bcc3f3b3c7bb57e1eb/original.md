Arguments:

  * `attachments::Vector{_AttachmentDescription2}`
  * `subpasses::Vector{_SubpassDescription2}`
  * `dependencies::Vector{_SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo2.html)

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
