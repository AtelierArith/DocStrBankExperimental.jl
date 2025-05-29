High-level wrapper for VkFramebufferCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferCreateInfo.html)

```julia
struct FramebufferCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.FramebufferCreateFlag`
  * `render_pass::Vulkan.RenderPass`
  * `attachments::Vector{Vulkan.ImageView}`
  * `width::UInt32`
  * `height::UInt32`
  * `layers::UInt32`
