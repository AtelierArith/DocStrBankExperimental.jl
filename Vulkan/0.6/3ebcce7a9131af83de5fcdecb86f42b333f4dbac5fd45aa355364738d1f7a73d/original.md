High-level wrapper for VkRenderPassSubpassFeedbackInfoEXT.

Extension: VK_EXT_subpass_merge_feedback

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSubpassFeedbackInfoEXT.html)

```julia
struct RenderPassSubpassFeedbackInfoEXT <: Vulkan.HighLevelStruct
```

  * `subpass_merge_status::Vulkan.SubpassMergeStatusEXT`
  * `description::String`
  * `post_merge_index::UInt32`
