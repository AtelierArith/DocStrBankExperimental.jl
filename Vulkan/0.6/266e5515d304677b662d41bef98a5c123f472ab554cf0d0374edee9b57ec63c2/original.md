Arguments:

  * `device::Device`
  * `attachments::Vector{AttachmentDescription2}`
  * `subpasses::Vector{SubpassDescription2}`
  * `dependencies::Vector{SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass2.html)

```julia
RenderPass(
    device,
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray,
    correlated_view_masks::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.RenderPass

```
