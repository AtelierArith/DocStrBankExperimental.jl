VkAttachmentReference2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentReference2.html)

```julia
struct AttachmentReference2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `attachment::UInt32`
  * `layout::Vulkan.ImageLayout`
  * `aspect_mask::Vulkan.ImageAspectFlag`
