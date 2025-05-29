VkClearAttachmentの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkClearAttachment.html)

```julia
struct ClearAttachment <: Vulkan.HighLevelStruct
```

  * `aspect_mask::Vulkan.ImageAspectFlag`
  * `color_attachment::UInt32`
  * `clear_value::Vulkan.ClearValue`
