VkRenderPassSubpassFeedbackInfoEXTの高レベルラッパー。

拡張: VK*EXT*subpass*merge*feedback

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSubpassFeedbackInfoEXT.html)

```julia
struct RenderPassSubpassFeedbackInfoEXT <: Vulkan.HighLevelStruct
```

  * `subpass_merge_status::Vulkan.SubpassMergeStatusEXT`
  * `description::String`
  * `post_merge_index::UInt32`
