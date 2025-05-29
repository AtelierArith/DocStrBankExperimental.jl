引数:

  * `render_pass::RenderPass`
  * `attachments::Vector{ImageView}`
  * `width::UInt32`
  * `height::UInt32`
  * `layers::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::FramebufferCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferCreateInfo.html)

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
