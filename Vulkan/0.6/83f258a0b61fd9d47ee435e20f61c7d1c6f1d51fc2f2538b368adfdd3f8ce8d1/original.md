Extension: VK_QCOM_render_pass_transform

Arguments:

  * `transform::SurfaceTransformFlagKHR`
  * `render_area::Rect2D`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderPassTransformInfoQCOM.html)

```julia
CommandBufferInheritanceRenderPassTransformInfoQCOM(
    transform::Vulkan.SurfaceTransformFlagKHR,
    render_area::Vulkan.Rect2D;
    next
) -> Vulkan.CommandBufferInheritanceRenderPassTransformInfoQCOM

```
