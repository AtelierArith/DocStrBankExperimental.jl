High-level wrapper for VkResolveImageInfo2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkResolveImageInfo2.html)

```julia
struct ResolveImageInfo2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_image::Vulkan.Image`
  * `src_image_layout::Vulkan.ImageLayout`
  * `dst_image::Vulkan.Image`
  * `dst_image_layout::Vulkan.ImageLayout`
  * `regions::Vector{Vulkan.ImageResolve2}`
