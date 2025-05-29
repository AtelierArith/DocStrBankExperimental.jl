High-level wrapper for VkPipelineRenderingCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRenderingCreateInfo.html)

```julia
struct PipelineRenderingCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `view_mask::UInt32`
  * `color_attachment_formats::Vector{Vulkan.Format}`
  * `depth_attachment_format::Vulkan.Format`
  * `stencil_attachment_format::Vulkan.Format`
