引数:

  * `image_layout::ImageLayout`
  * `resolve_image_layout::ImageLayout`
  * `load_op::AttachmentLoadOp`
  * `store_op::AttachmentStoreOp`
  * `clear_value::_ClearValue`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `image_view::ImageView`: デフォルトは `C_NULL`
  * `resolve_mode::ResolveModeFlag`: デフォルトは `0`
  * `resolve_image_view::ImageView`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingAttachmentInfo.html)

```julia
_RenderingAttachmentInfo(
    image_layout::Vulkan.ImageLayout,
    resolve_image_layout::Vulkan.ImageLayout,
    load_op::Vulkan.AttachmentLoadOp,
    store_op::Vulkan.AttachmentStoreOp,
    clear_value::Vulkan._ClearValue;
    next,
    image_view,
    resolve_mode,
    resolve_image_view
)

```
