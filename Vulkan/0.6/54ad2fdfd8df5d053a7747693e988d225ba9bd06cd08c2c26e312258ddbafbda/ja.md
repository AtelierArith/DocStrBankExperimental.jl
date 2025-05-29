引数:

  * `attachment_image_infos::Vector{FramebufferAttachmentImageInfo}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentsCreateInfo.html)

```julia
FramebufferAttachmentsCreateInfo(
    attachment_image_infos::AbstractArray;
    next
) -> Vulkan.FramebufferAttachmentsCreateInfo

```
