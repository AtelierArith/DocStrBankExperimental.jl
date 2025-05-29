引数:

  * `attachment::UInt32`
  * `layout::ImageLayout`
  * `aspect_mask::ImageAspectFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentReference2.html)

```julia
AttachmentReference2(
    attachment::Integer,
    layout::Vulkan.ImageLayout,
    aspect_mask::Vulkan.ImageAspectFlag;
    next
) -> Vulkan.AttachmentReference2

```
