Arguments:

  * `view_mask::UInt32`
  * `color_attachment_formats::Vector{Format}`
  * `depth_attachment_format::Format`
  * `stencil_attachment_format::Format`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRenderingCreateInfo.html)

```julia
PipelineRenderingCreateInfo(
    view_mask::Integer,
    color_attachment_formats::AbstractArray,
    depth_attachment_format::Vulkan.Format,
    stencil_attachment_format::Vulkan.Format;
    next
) -> Vulkan.PipelineRenderingCreateInfo

```
