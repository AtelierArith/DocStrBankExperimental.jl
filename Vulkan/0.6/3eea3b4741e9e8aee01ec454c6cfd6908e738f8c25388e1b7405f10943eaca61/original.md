Extension: VK_EXT_display_surface_counter

Arguments:

  * `min_image_count::UInt32`
  * `max_image_count::UInt32`
  * `current_extent::Extent2D`
  * `min_image_extent::Extent2D`
  * `max_image_extent::Extent2D`
  * `max_image_array_layers::UInt32`
  * `supported_transforms::SurfaceTransformFlagKHR`
  * `current_transform::SurfaceTransformFlagKHR`
  * `supported_composite_alpha::CompositeAlphaFlagKHR`
  * `supported_usage_flags::ImageUsageFlag`
  * `next::Any`: defaults to `C_NULL`
  * `supported_surface_counters::SurfaceCounterFlagEXT`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilities2EXT.html)

```julia
SurfaceCapabilities2EXT(
    min_image_count::Integer,
    max_image_count::Integer,
    current_extent::Vulkan.Extent2D,
    min_image_extent::Vulkan.Extent2D,
    max_image_extent::Vulkan.Extent2D,
    max_image_array_layers::Integer,
    supported_transforms::Vulkan.SurfaceTransformFlagKHR,
    current_transform::Vulkan.SurfaceTransformFlagKHR,
    supported_composite_alpha::Vulkan.CompositeAlphaFlagKHR,
    supported_usage_flags::Vulkan.ImageUsageFlag;
    next,
    supported_surface_counters
) -> Vulkan.SurfaceCapabilities2EXT

```
