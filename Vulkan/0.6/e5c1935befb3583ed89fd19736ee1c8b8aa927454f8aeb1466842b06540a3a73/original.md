Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

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
_create_render_pass_2(
    device,
    attachments::AbstractArray,
    subpasses::AbstractArray,
    dependencies::AbstractArray,
    correlated_view_masks::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.RenderPass, Vulkan.VulkanError}

```
