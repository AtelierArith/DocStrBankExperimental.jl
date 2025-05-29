Arguments:

  * `format::Format`
  * `samples::SampleCountFlag`
  * `load_op::AttachmentLoadOp`
  * `store_op::AttachmentStoreOp`
  * `stencil_load_op::AttachmentLoadOp`
  * `stencil_store_op::AttachmentStoreOp`
  * `initial_layout::ImageLayout`
  * `final_layout::ImageLayout`
  * `flags::AttachmentDescriptionFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentDescription.html)

```julia
AttachmentDescription(
    format::Vulkan.Format,
    samples::Vulkan.SampleCountFlag,
    load_op::Vulkan.AttachmentLoadOp,
    store_op::Vulkan.AttachmentStoreOp,
    stencil_load_op::Vulkan.AttachmentLoadOp,
    stencil_store_op::Vulkan.AttachmentStoreOp,
    initial_layout::Vulkan.ImageLayout,
    final_layout::Vulkan.ImageLayout;
    flags
) -> Vulkan.AttachmentDescription

```
