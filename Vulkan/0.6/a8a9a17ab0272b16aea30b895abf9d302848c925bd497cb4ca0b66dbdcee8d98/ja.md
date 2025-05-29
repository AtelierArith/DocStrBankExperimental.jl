VkRenderPassAttachmentBeginInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassAttachmentBeginInfo.html)

```julia
struct RenderPassAttachmentBeginInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `attachments::Vector{Vulkan.ImageView}`
