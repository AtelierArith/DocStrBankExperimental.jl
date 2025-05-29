拡張: VK*EXT*surface_maintenance1

引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `supported_present_scaling::PresentScalingFlagEXT`: デフォルトは `0`
  * `supported_present_gravity_x::PresentGravityFlagEXT`: デフォルトは `0`
  * `supported_present_gravity_y::PresentGravityFlagEXT`: デフォルトは `0`
  * `min_scaled_image_extent::Extent2D`: デフォルトは `C_NULL`
  * `max_scaled_image_extent::Extent2D`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentScalingCapabilitiesEXT.html)

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
