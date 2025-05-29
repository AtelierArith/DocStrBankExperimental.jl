引数:

  * `render_pass::RenderPass`
  * `framebuffer::Framebuffer`
  * `render_area::Rect2D`
  * `clear_values::Vector{ClearValue}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassBeginInfo.html)

```julia
RenderPassBeginInfo(
    render_pass::Vulkan.RenderPass,
    framebuffer::Vulkan.Framebuffer,
    render_area::Vulkan.Rect2D,
    clear_values::AbstractArray;
    next
) -> Vulkan.RenderPassBeginInfo

```
