High-level wrapper for VkFramebufferAttachmentImageInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFramebufferAttachmentImageInfo.html)

```julia
struct FramebufferAttachmentImageInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.ImageCreateFlag`
  * `usage::Vulkan.ImageUsageFlag`
  * `width::UInt32`
  * `height::UInt32`
  * `layer_count::UInt32`
  * `view_formats::Vector{Vulkan.Format}`
