高レベルのラッパー VkImageCreateInfo。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageCreateInfo.html)

```julia
struct ImageCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.ImageCreateFlag`
  * `image_type::Vulkan.ImageType`
  * `format::Vulkan.Format`
  * `extent::Vulkan.Extent3D`
  * `mip_levels::UInt32`
  * `array_layers::UInt32`
  * `samples::Vulkan.SampleCountFlag`
  * `tiling::Vulkan.ImageTiling`
  * `usage::Vulkan.ImageUsageFlag`
  * `sharing_mode::Vulkan.SharingMode`
  * `queue_family_indices::Vector{UInt32}`
  * `initial_layout::Vulkan.ImageLayout`
