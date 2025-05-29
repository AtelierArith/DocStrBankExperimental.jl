Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `instance::Instance`
  * `display_mode::DisplayModeKHR`
  * `plane_index::UInt32`
  * `plane_stack_index::UInt32`
  * `transform::SurfaceTransformFlagKHR`
  * `global_alpha::Float32`
  * `alpha_mode::DisplayPlaneAlphaFlagKHR`
  * `image_extent::_Extent2D`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayPlaneSurfaceKHR.html)

```julia
_create_display_plane_surface_khr(
    instance,
    display_mode,
    plane_index::Integer,
    plane_stack_index::Integer,
    transform::Vulkan.SurfaceTransformFlagKHR,
    global_alpha::Real,
    alpha_mode::Vulkan.DisplayPlaneAlphaFlagKHR,
    image_extent::Vulkan._Extent2D;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
