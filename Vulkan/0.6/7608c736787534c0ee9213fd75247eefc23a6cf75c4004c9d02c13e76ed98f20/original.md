Extension: VK_KHR_dynamic_rendering

Arguments:

  * `color_attachment_samples::Vector{SampleCountFlag}`
  * `next::Any`: defaults to `C_NULL`
  * `depth_stencil_attachment_samples::SampleCountFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentSampleCountInfoAMD.html)

```julia
AttachmentSampleCountInfoAMD(
    color_attachment_samples::AbstractArray;
    next,
    depth_stencil_attachment_samples
) -> Vulkan.AttachmentSampleCountInfoAMD

```
