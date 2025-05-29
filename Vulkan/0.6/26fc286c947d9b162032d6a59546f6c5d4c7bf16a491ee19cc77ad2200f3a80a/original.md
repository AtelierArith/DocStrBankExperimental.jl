Arguments:

  * `device::Device`
  * `attachments::Vector{_AttachmentDescription2}`
  * `subpasses::Vector{_SubpassDescription2}`
  * `dependencies::Vector{_SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass2.html)

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
