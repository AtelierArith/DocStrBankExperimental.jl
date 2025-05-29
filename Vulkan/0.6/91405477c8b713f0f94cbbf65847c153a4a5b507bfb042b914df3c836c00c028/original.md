Arguments:

  * `device::Device`
  * `attachments::Vector{_AttachmentDescription}`
  * `subpasses::Vector{_SubpassDescription}`
  * `dependencies::Vector{_SubpassDependency}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::RenderPassCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass.html)

```julia
RenderPass(
    device,
    attachments::AbstractArray{Vulkan._AttachmentDescription},
    subpasses::AbstractArray{Vulkan._SubpassDescription},
    dependencies::AbstractArray{Vulkan._SubpassDependency};
    allocator,
    next,
    flags
) -> Vulkan.RenderPass

```
