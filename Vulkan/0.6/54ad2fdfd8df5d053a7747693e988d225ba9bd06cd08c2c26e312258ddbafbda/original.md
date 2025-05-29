Arguments:

  * `attachment_image_infos::Vector{FramebufferAttachmentImageInfo}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentsCreateInfo.html)

```julia
FramebufferAttachmentsCreateInfo(
    attachment_image_infos::AbstractArray;
    next
) -> Vulkan.FramebufferAttachmentsCreateInfo

```
