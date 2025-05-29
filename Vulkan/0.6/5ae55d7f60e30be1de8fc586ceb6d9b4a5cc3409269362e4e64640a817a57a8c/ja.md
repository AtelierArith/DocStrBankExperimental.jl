VkCopyMemoryToImageIndirectCommandNVの高レベルラッパー。

拡張: VK*NV*copy*memory*indirect

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMemoryToImageIndirectCommandNV.html)

```julia
struct CopyMemoryToImageIndirectCommandNV <: Vulkan.HighLevelStruct
```

  * `src_address::UInt64`
  * `buffer_row_length::UInt32`
  * `buffer_image_height::UInt32`
  * `image_subresource::Vulkan.ImageSubresourceLayers`
  * `image_offset::Vulkan.Offset3D`
  * `image_extent::Vulkan.Extent3D`
