Arguments:

  * `device::Device`
  * `render_pass::RenderPass`
  * `attachments::Vector{ImageView}`
  * `width::UInt32`
  * `height::UInt32`
  * `layers::UInt32`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::FramebufferCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateFramebuffer.html)

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
