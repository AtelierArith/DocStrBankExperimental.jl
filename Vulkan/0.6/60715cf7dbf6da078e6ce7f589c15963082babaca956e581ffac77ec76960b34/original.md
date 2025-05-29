High-level wrapper for VkAttachmentDescription.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentDescription.html)

```julia
struct AttachmentDescription <: Vulkan.HighLevelStruct
```

  * `flags::Vulkan.AttachmentDescriptionFlag`
  * `format::Vulkan.Format`
  * `samples::Vulkan.SampleCountFlag`
  * `load_op::Vulkan.AttachmentLoadOp`
  * `store_op::Vulkan.AttachmentStoreOp`
  * `stencil_load_op::Vulkan.AttachmentLoadOp`
  * `stencil_store_op::Vulkan.AttachmentStoreOp`
  * `initial_layout::Vulkan.ImageLayout`
  * `final_layout::Vulkan.ImageLayout`
