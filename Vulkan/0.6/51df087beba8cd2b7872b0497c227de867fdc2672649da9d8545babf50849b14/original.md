High-level wrapper for VkCopyImageInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyImageInfo2.html)

```julia
struct CopyImageInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_image::Vulkan.Image`
  * `src_image_layout::Vulkan.ImageLayout`
  * `dst_image::Vulkan.Image`
  * `dst_image_layout::Vulkan.ImageLayout`
  * `regions::Vector{Vulkan.ImageCopy2}`
