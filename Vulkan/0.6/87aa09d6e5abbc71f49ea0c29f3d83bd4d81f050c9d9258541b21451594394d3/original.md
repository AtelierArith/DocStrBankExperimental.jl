Extension: VK_QCOM_render_pass_transform

Arguments:

  * `transform::SurfaceTransformFlagKHR`
  * `render_area::_Rect2D`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderPassTransformInfoQCOM.html)

```julia
_CommandBufferInheritanceRenderPassTransformInfoQCOM(
    transform::Vulkan.SurfaceTransformFlagKHR,
    render_area::Vulkan._Rect2D;
    next
) -> Vulkan._CommandBufferInheritanceRenderPassTransformInfoQCOM

```
