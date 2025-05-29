High-level wrapper for VkImageCopy.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCopy.html)

```julia
struct ImageCopy <: Vulkan.HighLevelStruct
```

  * `src_subresource::Vulkan.ImageSubresourceLayers`
  * `src_offset::Vulkan.Offset3D`
  * `dst_subresource::Vulkan.ImageSubresourceLayers`
  * `dst_offset::Vulkan.Offset3D`
  * `extent::Vulkan.Extent3D`
