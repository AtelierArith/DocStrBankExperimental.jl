Extension: VK_EXT_conditional_rendering

Arguments:

  * `conditional_rendering_enable::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceConditionalRenderingInfoEXT.html)

```julia
_CommandBufferInheritanceConditionalRenderingInfoEXT(
    conditional_rendering_enable::Bool;
    next
) -> Vulkan._CommandBufferInheritanceConditionalRenderingInfoEXT

```
