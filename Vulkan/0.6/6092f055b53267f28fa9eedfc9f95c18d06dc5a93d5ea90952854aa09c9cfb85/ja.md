VkSurfaceCapabilities2EXTの高レベルラッパー。

拡張: VK*EXT*display*surface*counter

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilities2EXT.html)

```julia
struct SurfaceCapabilities2EXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `min_image_count::UInt32`
  * `max_image_count::UInt32`
  * `current_extent::Vulkan.Extent2D`
  * `min_image_extent::Vulkan.Extent2D`
  * `max_image_extent::Vulkan.Extent2D`
  * `max_image_array_layers::UInt32`
  * `supported_transforms::Vulkan.SurfaceTransformFlagKHR`
  * `current_transform::Vulkan.SurfaceTransformFlagKHR`
  * `supported_composite_alpha::Vulkan.CompositeAlphaFlagKHR`
  * `supported_usage_flags::Vulkan.ImageUsageFlag`
  * `supported_surface_counters::Vulkan.SurfaceCounterFlagEXT`
