High-level wrapper for VkCopyBufferToImageInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferToImageInfo2.html)

```julia
struct CopyBufferToImageInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_buffer::Vulkan.Buffer`
  * `dst_image::Vulkan.Image`
  * `dst_image_layout::Vulkan.ImageLayout`
  * `regions::Vector{Vulkan.BufferImageCopy2}`
