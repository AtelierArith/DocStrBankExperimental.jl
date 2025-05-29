High-level wrapper for VkRenderingAttachmentInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderingAttachmentInfo.html)

```julia
struct RenderingAttachmentInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image_view::Union{Ptr{Nothing}, Vulkan.ImageView}`
  * `image_layout::Vulkan.ImageLayout`
  * `resolve_mode::Vulkan.ResolveModeFlag`
  * `resolve_image_view::Union{Ptr{Nothing}, Vulkan.ImageView}`
  * `resolve_image_layout::Vulkan.ImageLayout`
  * `load_op::Vulkan.AttachmentLoadOp`
  * `store_op::Vulkan.AttachmentStoreOp`
  * `clear_value::Vulkan.ClearValue`
