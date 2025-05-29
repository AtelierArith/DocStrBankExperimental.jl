引数:

  * `device::Device`
  * `attachments::Vector{AttachmentDescription}`
  * `subpasses::Vector{SubpassDescription}`
  * `dependencies::Vector{SubpassDependency}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::RenderPassCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass.html)

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
