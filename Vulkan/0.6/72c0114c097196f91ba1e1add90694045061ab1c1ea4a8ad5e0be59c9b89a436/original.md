Extension: VK_KHR_surface

Arguments:

  * `min_image_count::UInt32`
  * `max_image_count::UInt32`
  * `current_extent::_Extent2D`
  * `min_image_extent::_Extent2D`
  * `max_image_extent::_Extent2D`
  * `max_image_array_layers::UInt32`
  * `supported_transforms::SurfaceTransformFlagKHR`
  * `current_transform::SurfaceTransformFlagKHR`
  * `supported_composite_alpha::CompositeAlphaFlagKHR`
  * `supported_usage_flags::ImageUsageFlag`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilitiesKHR.html)

```julia
_SurfaceCapabilitiesKHR(
    min_image_count::Integer,
    max_image_count::Integer,
    current_extent::Vulkan._Extent2D,
    min_image_extent::Vulkan._Extent2D,
    max_image_extent::Vulkan._Extent2D,
    max_image_array_layers::Integer,
    supported_transforms::Vulkan.SurfaceTransformFlagKHR,
    current_transform::Vulkan.SurfaceTransformFlagKHR,
    supported_composite_alpha::Vulkan.CompositeAlphaFlagKHR,
    supported_usage_flags::Vulkan.ImageUsageFlag
) -> Vulkan._SurfaceCapabilitiesKHR

```
