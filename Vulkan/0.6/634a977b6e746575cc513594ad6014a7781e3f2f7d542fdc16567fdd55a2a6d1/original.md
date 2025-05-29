High-level wrapper for VkCommandBufferInheritanceRenderingInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderingInfo.html)

```julia
struct CommandBufferInheritanceRenderingInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.RenderingFlag`
  * `view_mask::UInt32`
  * `color_attachment_formats::Vector{Vulkan.Format}`
  * `depth_attachment_format::Vulkan.Format`
  * `stencil_attachment_format::Vulkan.Format`
  * `rasterization_samples::Vulkan.SampleCountFlag`
