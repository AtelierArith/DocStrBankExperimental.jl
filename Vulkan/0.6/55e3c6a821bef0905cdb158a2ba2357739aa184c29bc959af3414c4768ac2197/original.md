High-level wrapper for VkAttachmentSampleCountInfoAMD.

Extension: VK_KHR_dynamic_rendering

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentSampleCountInfoAMD.html)

```julia
struct AttachmentSampleCountInfoAMD <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `color_attachment_samples::Vector{Vulkan.SampleCountFlag}`
  * `depth_stencil_attachment_samples::Vulkan.SampleCountFlag`
