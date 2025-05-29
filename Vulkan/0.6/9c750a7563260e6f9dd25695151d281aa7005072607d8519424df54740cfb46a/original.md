High-level wrapper for VkCommandBufferInheritanceRenderPassTransformInfoQCOM.

Extension: VK_QCOM_render_pass_transform

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderPassTransformInfoQCOM.html)

```julia
struct CommandBufferInheritanceRenderPassTransformInfoQCOM <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `transform::Vulkan.SurfaceTransformFlagKHR`
  * `render_area::Vulkan.Rect2D`
