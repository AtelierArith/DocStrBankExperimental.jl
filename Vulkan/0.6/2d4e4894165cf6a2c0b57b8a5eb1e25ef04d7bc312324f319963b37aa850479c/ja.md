VkFragmentShadingRateAttachmentInfoKHRの高レベルラッパー。

拡張: VK*KHR*fragment*shading*rate

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkFragmentShadingRateAttachmentInfoKHR.html)

```julia
struct FragmentShadingRateAttachmentInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `fragment_shading_rate_attachment::Union{Ptr{Nothing}, Vulkan.AttachmentReference2}`
  * `shading_rate_attachment_texel_size::Vulkan.Extent2D`
