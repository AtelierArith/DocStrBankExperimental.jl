Arguments:

  * `render_pass::RenderPass`
  * `attachments::Vector{ImageView}`
  * `width::UInt32`
  * `height::UInt32`
  * `layers::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::FramebufferCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferCreateInfo.html)

```julia
_FramebufferCreateInfo(
    render_pass,
    attachments::AbstractArray,
    width::Integer,
    height::Integer,
    layers::Integer;
    next,
    flags
) -> Vulkan._FramebufferCreateInfo

```
