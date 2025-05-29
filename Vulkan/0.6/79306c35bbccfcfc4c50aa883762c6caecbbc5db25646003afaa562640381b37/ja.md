戻り値のコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `render_pass::RenderPass`
  * `attachments::Vector{ImageView}`
  * `width::UInt32`
  * `height::UInt32`
  * `layers::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::FramebufferCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateFramebuffer.html)

```julia
create_framebuffer(
    device,
    render_pass,
    attachments::AbstractArray,
    width::Integer,
    height::Integer,
    layers::Integer;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.Framebuffer, Vulkan.VulkanError}

```
