Arguments:

  * `image_layout::ImageLayout`
  * `resolve_image_layout::ImageLayout`
  * `load_op::AttachmentLoadOp`
  * `store_op::AttachmentStoreOp`
  * `clear_value::ClearValue`
  * `next::Any`: defaults to `C_NULL`
  * `image_view::ImageView`: defaults to `C_NULL`
  * `resolve_mode::ResolveModeFlag`: defaults to `0`
  * `resolve_image_view::ImageView`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingAttachmentInfo.html)

```julia
RenderingAttachmentInfo(
    image_layout::Vulkan.ImageLayout,
    resolve_image_layout::Vulkan.ImageLayout,
    load_op::Vulkan.AttachmentLoadOp,
    store_op::Vulkan.AttachmentStoreOp,
    clear_value::Vulkan.ClearValue;
    next,
    image_view,
    resolve_mode,
    resolve_image_view
) -> Vulkan.RenderingAttachmentInfo

```
