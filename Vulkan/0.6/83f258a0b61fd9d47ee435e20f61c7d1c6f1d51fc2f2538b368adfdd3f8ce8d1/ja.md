拡張: VK*QCOM*render*pass*transform

引数:

  * `transform::SurfaceTransformFlagKHR`
  * `render_area::Rect2D`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderPassTransformInfoQCOM.html)

```julia
CommandBufferInheritanceRenderPassTransformInfoQCOM(
    transform::Vulkan.SurfaceTransformFlagKHR,
    render_area::Vulkan.Rect2D;
    next
) -> Vulkan.CommandBufferInheritanceRenderPassTransformInfoQCOM

```
