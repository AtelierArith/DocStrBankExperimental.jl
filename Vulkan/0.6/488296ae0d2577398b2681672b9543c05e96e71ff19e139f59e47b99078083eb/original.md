Extension: VK_KHR_display

Arguments:

  * `display_mode::DisplayModeKHR`
  * `plane_index::UInt32`
  * `plane_stack_index::UInt32`
  * `transform::SurfaceTransformFlagKHR`
  * `global_alpha::Float32`
  * `alpha_mode::DisplayPlaneAlphaFlagKHR`
  * `image_extent::Extent2D`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplaySurfaceCreateInfoKHR.html)

```julia
DisplaySurfaceCreateInfoKHR(
    display_mode::Vulkan.DisplayModeKHR,
    plane_index::Integer,
    plane_stack_index::Integer,
    transform::Vulkan.SurfaceTransformFlagKHR,
    global_alpha::Real,
    alpha_mode::Vulkan.DisplayPlaneAlphaFlagKHR,
    image_extent::Vulkan.Extent2D;
    next,
    flags
) -> Vulkan.DisplaySurfaceCreateInfoKHR

```
