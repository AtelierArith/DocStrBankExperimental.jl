VkImageFormatPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageFormatProperties.html)

```julia
struct ImageFormatProperties <: Vulkan.HighLevelStruct
```

  * `max_extent::Vulkan.Extent3D`
  * `max_mip_levels::UInt32`
  * `max_array_layers::UInt32`
  * `sample_counts::Vulkan.SampleCountFlag`
  * `max_resource_size::UInt64`
