VkInputAttachmentAspectReferenceの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkInputAttachmentAspectReference.html)

```julia
struct InputAttachmentAspectReference <: Vulkan.HighLevelStruct
```

  * `subpass::UInt32`
  * `input_attachment_index::UInt32`
  * `aspect_mask::Vulkan.ImageAspectFlag`
