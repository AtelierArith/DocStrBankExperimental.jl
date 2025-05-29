拡張: VK*KHR*dynamic_rendering

引数:

  * `color_attachment_samples::Vector{SampleCountFlag}`
  * `next::Any`: デフォルトは `C_NULL`
  * `depth_stencil_attachment_samples::SampleCountFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentSampleCountInfoAMD.html)

```julia
AttachmentSampleCountInfoAMD(
    color_attachment_samples::AbstractArray;
    next,
    depth_stencil_attachment_samples
) -> Vulkan.AttachmentSampleCountInfoAMD

```
