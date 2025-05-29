High-level wrapper for VkSurfaceCapabilities2EXT.

Extension: VK_EXT_display_surface_counter

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilities2EXT.html)

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
