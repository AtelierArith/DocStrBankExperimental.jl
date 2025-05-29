Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

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
_create_render_pass(
    device,
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.RenderPass, Vulkan.VulkanError}

```
