引数:

  * `stencil_initial_layout::ImageLayout`
  * `stencil_final_layout::ImageLayout`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentDescriptionStencilLayout.html)

```julia
_AttachmentDescriptionStencilLayout(
    stencil_initial_layout::Vulkan.ImageLayout,
    stencil_final_layout::Vulkan.ImageLayout;
    next
) -> Vulkan._AttachmentDescriptionStencilLayout

```
