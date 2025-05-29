High-level wrapper for VkSubpassDescription2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescription2.html)

```julia
struct SubpassDescription2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.SubpassDescriptionFlag`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `view_mask::UInt32`
  * `input_attachments::Vector{Vulkan.AttachmentReference2}`
  * `color_attachments::Vector{Vulkan.AttachmentReference2}`
  * `resolve_attachments::Union{Ptr{Nothing}, Vector{Vulkan.AttachmentReference2}}`
  * `depth_stencil_attachment::Union{Ptr{Nothing}, Vulkan.AttachmentReference2}`
  * `preserve_attachments::Vector{UInt32}`
