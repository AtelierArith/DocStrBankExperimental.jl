Arguments:

  * `stencil_initial_layout::ImageLayout`
  * `stencil_final_layout::ImageLayout`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentDescriptionStencilLayout.html)

```julia
AttachmentDescriptionStencilLayout(
    stencil_initial_layout::Vulkan.ImageLayout,
    stencil_final_layout::Vulkan.ImageLayout;
    next
) -> Vulkan.AttachmentDescriptionStencilLayout

```
