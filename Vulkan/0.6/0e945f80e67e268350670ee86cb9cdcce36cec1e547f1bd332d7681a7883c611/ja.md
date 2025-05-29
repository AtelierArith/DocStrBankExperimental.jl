引数:

  * `format::Format`
  * `samples::SampleCountFlag`
  * `load_op::AttachmentLoadOp`
  * `store_op::AttachmentStoreOp`
  * `stencil_load_op::AttachmentLoadOp`
  * `stencil_store_op::AttachmentStoreOp`
  * `initial_layout::ImageLayout`
  * `final_layout::ImageLayout`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::AttachmentDescriptionFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentDescription2.html)

```julia
AttachmentDescription2(
    format::Vulkan.Format,
    samples::Vulkan.SampleCountFlag,
    load_op::Vulkan.AttachmentLoadOp,
    store_op::Vulkan.AttachmentStoreOp,
    stencil_load_op::Vulkan.AttachmentLoadOp,
    stencil_store_op::Vulkan.AttachmentStoreOp,
    initial_layout::Vulkan.ImageLayout,
    final_layout::Vulkan.ImageLayout;
    next,
    flags
) -> Vulkan.AttachmentDescription2

```
