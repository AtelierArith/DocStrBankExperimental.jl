Extension: VK_EXT_subpass_merge_feedback

Arguments:

  * `render_pass_feedback::_RenderPassCreationFeedbackInfoEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreationFeedbackCreateInfoEXT.html)

```julia
_RenderPassCreationFeedbackCreateInfoEXT(
    render_pass_feedback::Vulkan._RenderPassCreationFeedbackInfoEXT;
    next
) -> Vulkan._RenderPassCreationFeedbackCreateInfoEXT

```
