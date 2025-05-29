Extension: VK_EXT_subpass_merge_feedback

Arguments:

  * `subpass_feedback::_RenderPassSubpassFeedbackInfoEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassSubpassFeedbackCreateInfoEXT.html)

```julia
_RenderPassSubpassFeedbackCreateInfoEXT(
    subpass_feedback::Vulkan._RenderPassSubpassFeedbackInfoEXT;
    next
) -> Vulkan._RenderPassSubpassFeedbackCreateInfoEXT

```
