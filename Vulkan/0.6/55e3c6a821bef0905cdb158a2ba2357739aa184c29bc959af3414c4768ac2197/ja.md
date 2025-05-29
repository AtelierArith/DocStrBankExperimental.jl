VkAttachmentSampleCountInfoAMDの高レベルラッパー。

拡張: VK*KHR*dynamic_rendering

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAttachmentSampleCountInfoAMD.html)

```julia
struct AttachmentSampleCountInfoAMD <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `color_attachment_samples::Vector{Vulkan.SampleCountFlag}`
  * `depth_stencil_attachment_samples::Vulkan.SampleCountFlag`
