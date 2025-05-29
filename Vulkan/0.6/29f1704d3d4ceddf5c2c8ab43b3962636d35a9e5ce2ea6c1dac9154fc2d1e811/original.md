Extension: VK_EXT_extended_dynamic_state3

Arguments:

  * `src_color_blend_factor::BlendFactor`
  * `dst_color_blend_factor::BlendFactor`
  * `color_blend_op::BlendOp`
  * `src_alpha_blend_factor::BlendFactor`
  * `dst_alpha_blend_factor::BlendFactor`
  * `alpha_blend_op::BlendOp`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkColorBlendEquationEXT.html)

```julia
_ColorBlendEquationEXT(
    src_color_blend_factor::Vulkan.BlendFactor,
    dst_color_blend_factor::Vulkan.BlendFactor,
    color_blend_op::Vulkan.BlendOp,
    src_alpha_blend_factor::Vulkan.BlendFactor,
    dst_alpha_blend_factor::Vulkan.BlendFactor,
    alpha_blend_op::Vulkan.BlendOp
) -> Vulkan._ColorBlendEquationEXT

```
