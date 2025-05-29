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
Framebuffer(
    device,
    render_pass,
    attachments::AbstractArray,
    width::Integer,
    height::Integer,
    layers::Integer;
    allocator,
    next,
    flags
) -> Vulkan.Framebuffer

```
