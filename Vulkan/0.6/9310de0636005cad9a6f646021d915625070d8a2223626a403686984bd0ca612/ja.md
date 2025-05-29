VkRenderPassCreateInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreateInfo2.html)

```julia
struct RenderPassCreateInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.RenderPassCreateFlag`
  * `attachments::Vector{Vulkan.AttachmentDescription2}`
  * `subpasses::Vector{Vulkan.SubpassDescription2}`
  * `dependencies::Vector{Vulkan.SubpassDependency2}`
  * `correlated_view_masks::Vector{UInt32}`
