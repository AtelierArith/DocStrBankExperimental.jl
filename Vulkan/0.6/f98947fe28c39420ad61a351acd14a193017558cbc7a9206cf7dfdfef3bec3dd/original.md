High-level wrapper for VkRenderPassCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo.html)

```julia
struct RenderPassCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.RenderPassCreateFlag`
  * `attachments::Vector{Vulkan.AttachmentDescription}`
  * `subpasses::Vector{Vulkan.SubpassDescription}`
  * `dependencies::Vector{Vulkan.SubpassDependency}`
