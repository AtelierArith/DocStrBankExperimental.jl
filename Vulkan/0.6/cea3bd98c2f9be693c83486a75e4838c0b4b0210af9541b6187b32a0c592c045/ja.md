引数:

  * `view_mask::UInt32`
  * `color_attachment_formats::Vector{Format}`
  * `depth_attachment_format::Format`
  * `stencil_attachment_format::Format`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::RenderingFlag`: デフォルトは `0`
  * `rasterization_samples::SampleCountFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceRenderingInfo.html)

```julia
_CommandBufferInheritanceRenderingInfo(
    view_mask::Integer,
    color_attachment_formats::AbstractArray,
    depth_attachment_format::Vulkan.Format,
    stencil_attachment_format::Vulkan.Format;
    next,
    flags,
    rasterization_samples
)

```
