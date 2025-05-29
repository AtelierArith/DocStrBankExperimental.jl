VkSubpassDescriptionの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescription.html)

```julia
struct SubpassDescription <: Vulkan.HighLevelStruct
```

  * `flags::Vulkan.SubpassDescriptionFlag`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `input_attachments::Vector{Vulkan.AttachmentReference}`
  * `color_attachments::Vector{Vulkan.AttachmentReference}`
  * `resolve_attachments::Union{Ptr{Nothing}, Vector{Vulkan.AttachmentReference}}`
  * `depth_stencil_attachment::Union{Ptr{Nothing}, Vulkan.AttachmentReference}`
  * `preserve_attachments::Vector{UInt32}`
