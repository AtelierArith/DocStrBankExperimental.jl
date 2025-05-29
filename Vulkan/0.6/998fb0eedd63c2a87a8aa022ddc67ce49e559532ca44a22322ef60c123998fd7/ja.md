VkSparseImageFormatPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageFormatProperties.html)

```julia
struct SparseImageFormatProperties <: Vulkan.HighLevelStruct
```

  * `aspect_mask::Vulkan.ImageAspectFlag`
  * `image_granularity::Vulkan.Extent3D`
  * `flags::Vulkan.SparseImageFormatFlag`
