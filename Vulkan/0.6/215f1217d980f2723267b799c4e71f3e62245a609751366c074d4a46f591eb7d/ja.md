VkCopyImageToBufferInfo2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageToBufferInfo2.html)

```julia
struct CopyImageToBufferInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_image::Vulkan.Image`
  * `src_image_layout::Vulkan.ImageLayout`
  * `dst_buffer::Vulkan.Buffer`
  * `regions::Vector{Vulkan.BufferImageCopy2}`
