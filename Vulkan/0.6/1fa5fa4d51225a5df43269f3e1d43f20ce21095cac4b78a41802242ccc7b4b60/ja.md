VkRenderPassBeginInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassBeginInfo.html)

```julia
struct RenderPassBeginInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `render_pass::Vulkan.RenderPass`
  * `framebuffer::Vulkan.Framebuffer`
  * `render_area::Vulkan.Rect2D`
  * `clear_values::Vector{Vulkan.ClearValue}`
