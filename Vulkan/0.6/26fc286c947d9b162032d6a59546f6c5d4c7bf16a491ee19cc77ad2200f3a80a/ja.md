引数:

  * `device::Device`
  * `attachments::Vector{_AttachmentDescription2}`
  * `subpasses::Vector{_SubpassDescription2}`
  * `dependencies::Vector{_SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::RenderPassCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass2.html)

```julia
RenderPass(
    device,
    attachments::AbstractArray{Vulkan._AttachmentDescription2},
    subpasses::AbstractArray{Vulkan._SubpassDescription2},
    dependencies::AbstractArray{Vulkan._SubpassDependency2},
    correlated_view_masks::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.RenderPass

```
