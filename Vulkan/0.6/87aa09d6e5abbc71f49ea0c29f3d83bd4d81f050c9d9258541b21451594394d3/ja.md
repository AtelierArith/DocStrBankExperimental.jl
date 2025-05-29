拡張: VK*QCOM*render*pass*transform

引数:

  * `transform::SurfaceTransformFlagKHR`
  * `render_area::_Rect2D`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderPassTransformInfoQCOM.html)

```julia
_CommandBufferInheritanceRenderPassTransformInfoQCOM(
    transform::Vulkan.SurfaceTransformFlagKHR,
    render_area::Vulkan._Rect2D;
    next
) -> Vulkan._CommandBufferInheritanceRenderPassTransformInfoQCOM

```
