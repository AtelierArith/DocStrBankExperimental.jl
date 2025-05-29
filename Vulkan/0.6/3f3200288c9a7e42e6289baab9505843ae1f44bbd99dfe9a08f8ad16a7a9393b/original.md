Arguments:

  * `render_pass::RenderPass`
  * `framebuffer::Framebuffer`
  * `render_area::_Rect2D`
  * `clear_values::Vector{_ClearValue}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassBeginInfo.html)

```julia
_RenderPassBeginInfo(
    render_pass,
    framebuffer,
    render_area::Vulkan._Rect2D,
    clear_values::AbstractArray;
    next
) -> Vulkan._RenderPassBeginInfo

```
