Arguments:

  * `blend_enable::Bool`
  * `src_color_blend_factor::BlendFactor`
  * `dst_color_blend_factor::BlendFactor`
  * `color_blend_op::BlendOp`
  * `src_alpha_blend_factor::BlendFactor`
  * `dst_alpha_blend_factor::BlendFactor`
  * `alpha_blend_op::BlendOp`
  * `color_write_mask::ColorComponentFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendAttachmentState.html)

```julia
PipelineColorBlendAttachmentState(
    blend_enable::Bool,
    src_color_blend_factor::Vulkan.BlendFactor,
    dst_color_blend_factor::Vulkan.BlendFactor,
    color_blend_op::Vulkan.BlendOp,
    src_alpha_blend_factor::Vulkan.BlendFactor,
    dst_alpha_blend_factor::Vulkan.BlendFactor,
    alpha_blend_op::Vulkan.BlendOp;
    color_write_mask
) -> Vulkan.PipelineColorBlendAttachmentState

```
