Extension: VK_EXT_surface_maintenance1

Arguments:

  * `next::Any`: defaults to `C_NULL`
  * `supported_present_scaling::PresentScalingFlagEXT`: defaults to `0`
  * `supported_present_gravity_x::PresentGravityFlagEXT`: defaults to `0`
  * `supported_present_gravity_y::PresentGravityFlagEXT`: defaults to `0`
  * `min_scaled_image_extent::Extent2D`: defaults to `C_NULL`
  * `max_scaled_image_extent::Extent2D`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentScalingCapabilitiesEXT.html)

```julia
SurfacePresentScalingCapabilitiesEXT(
;
    next,
    supported_present_scaling,
    supported_present_gravity_x,
    supported_present_gravity_y,
    min_scaled_image_extent,
    max_scaled_image_extent
) -> Vulkan.SurfacePresentScalingCapabilitiesEXT

```
