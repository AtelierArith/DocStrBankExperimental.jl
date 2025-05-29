引数:

  * `attachment_image_infos::Vector{_FramebufferAttachmentImageInfo}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentsCreateInfo.html)

```julia
_FramebufferAttachmentsCreateInfo(
    attachment_image_infos::AbstractArray;
    next
) -> Vulkan._FramebufferAttachmentsCreateInfo

```
