Arguments:

  * `device::Device`
  * `attachments::Vector{AttachmentDescription}`
  * `subpasses::Vector{SubpassDescription}`
  * `dependencies::Vector{SubpassDependency}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass.html)

```julia
RenderPass(
    device,
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.RenderPass

```
