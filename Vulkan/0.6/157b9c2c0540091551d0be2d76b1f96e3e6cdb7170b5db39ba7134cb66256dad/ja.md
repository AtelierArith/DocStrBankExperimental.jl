VkSparseImageMemoryRequirementsの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryRequirements.html)

```julia
struct SparseImageMemoryRequirements <: Vulkan.HighLevelStruct
```

  * `format_properties::Vulkan.SparseImageFormatProperties`
  * `image_mip_tail_first_lod::UInt32`
  * `image_mip_tail_size::UInt64`
  * `image_mip_tail_offset::UInt64`
  * `image_mip_tail_stride::UInt64`
