引数:

  * `attachment::UInt32`
  * `layout::ImageLayout`
  * `aspect_mask::ImageAspectFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentReference2.html)

```julia
_AttachmentReference2(
    attachment::Integer,
    layout::Vulkan.ImageLayout,
    aspect_mask::Vulkan.ImageAspectFlag;
    next
) -> Vulkan._AttachmentReference2

```
