VkRenderingInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingInfo.html)

```julia
struct RenderingInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.RenderingFlag`
  * `render_area::Vulkan.Rect2D`
  * `layer_count::UInt32`
  * `view_mask::UInt32`
  * `color_attachments::Vector{Vulkan.RenderingAttachmentInfo}`
  * `depth_attachment::Union{Ptr{Nothing}, Vulkan.RenderingAttachmentInfo}`
  * `stencil_attachment::Union{Ptr{Nothing}, Vulkan.RenderingAttachmentInfo}`
