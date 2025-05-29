VkSurfaceCapabilitiesKHRの高レベルラッパー。

拡張: VK*KHR*surface

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilitiesKHR.html)

```julia
struct SurfaceCapabilitiesKHR <: Vulkan.HighLevelStruct
```

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
