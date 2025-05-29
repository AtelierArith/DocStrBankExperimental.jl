VkImageViewHandleInfoNVXの高レベルラッパー。

拡張: VK*NVX*image*view*handle

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageViewHandleInfoNVX.html)

```julia
struct ImageViewHandleInfoNVX <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `image_view::Vulkan.ImageView`
  * `descriptor_type::Vulkan.DescriptorType`
  * `sampler::Union{Ptr{Nothing}, Vulkan.Sampler}`
