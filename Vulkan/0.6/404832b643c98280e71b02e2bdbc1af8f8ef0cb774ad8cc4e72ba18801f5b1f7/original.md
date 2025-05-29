Arguments:

  * `attachment_image_infos::Vector{_FramebufferAttachmentImageInfo}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentsCreateInfo.html)

```julia
_FramebufferAttachmentsCreateInfo(
    attachment_image_infos::AbstractArray;
    next
) -> Vulkan._FramebufferAttachmentsCreateInfo

```
