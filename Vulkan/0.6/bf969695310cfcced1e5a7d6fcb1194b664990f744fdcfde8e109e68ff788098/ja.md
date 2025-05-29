VkBlitImageInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBlitImageInfo2.html)

```julia
struct BlitImageInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_image::Vulkan.Image`
  * `src_image_layout::Vulkan.ImageLayout`
  * `dst_image::Vulkan.Image`
  * `dst_image_layout::Vulkan.ImageLayout`
  * `regions::Vector{Vulkan.ImageBlit2}`
  * `filter::Vulkan.Filter`
