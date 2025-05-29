VkBufferImageCopyの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferImageCopy.html)

```julia
struct BufferImageCopy <: Vulkan.HighLevelStruct
```

  * `buffer_offset::UInt64`
  * `buffer_row_length::UInt32`
  * `buffer_image_height::UInt32`
  * `image_subresource::Vulkan.ImageSubresourceLayers`
  * `image_offset::Vulkan.Offset3D`
  * `image_extent::Vulkan.Extent3D`
