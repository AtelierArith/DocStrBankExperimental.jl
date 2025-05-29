VkImageCopy2の高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCopy2.html)

```julia
struct ImageCopy2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_subresource::Vulkan.ImageSubresourceLayers`
  * `src_offset::Vulkan.Offset3D`
  * `dst_subresource::Vulkan.ImageSubresourceLayers`
  * `dst_offset::Vulkan.Offset3D`
  * `extent::Vulkan.Extent3D`
