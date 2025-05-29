引数:

  * `stencil_layout::ImageLayout`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentReferenceStencilLayout.html)

```julia
_AttachmentReferenceStencilLayout(
    stencil_layout::Vulkan.ImageLayout;
    next
) -> Vulkan._AttachmentReferenceStencilLayout

```
