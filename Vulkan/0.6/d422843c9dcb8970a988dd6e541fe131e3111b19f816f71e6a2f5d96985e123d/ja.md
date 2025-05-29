戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `attachments::Vector{AttachmentDescription2}`
  * `subpasses::Vector{SubpassDescription2}`
  * `dependencies::Vector{SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::RenderPassCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateRenderPass2.html)

```julia
create_render_pass_2(
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
