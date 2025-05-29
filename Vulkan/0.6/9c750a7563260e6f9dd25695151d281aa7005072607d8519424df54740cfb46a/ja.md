VkCommandBufferInheritanceRenderPassTransformInfoQCOMの高レベルラッパー。

拡張: VK*QCOM*render*pass*transform

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderPassTransformInfoQCOM.html)

```julia
struct CommandBufferInheritanceRenderPassTransformInfoQCOM <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `transform::Vulkan.SurfaceTransformFlagKHR`
  * `render_area::Vulkan.Rect2D`
