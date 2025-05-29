VkPipelineColorBlendAttachmentStateの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendAttachmentState.html)

```julia
struct PipelineColorBlendAttachmentState <: Vulkan.HighLevelStruct
```

  * `blend_enable::Bool`
  * `src_color_blend_factor::Vulkan.BlendFactor`
  * `dst_color_blend_factor::Vulkan.BlendFactor`
  * `color_blend_op::Vulkan.BlendOp`
  * `src_alpha_blend_factor::Vulkan.BlendFactor`
  * `dst_alpha_blend_factor::Vulkan.BlendFactor`
  * `alpha_blend_op::Vulkan.BlendOp`
  * `color_write_mask::Vulkan.ColorComponentFlag`
