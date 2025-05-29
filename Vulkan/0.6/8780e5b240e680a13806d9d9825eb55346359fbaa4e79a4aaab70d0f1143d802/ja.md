拡張: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `instance::Instance`
  * `display_mode::DisplayModeKHR`
  * `plane_index::UInt32`
  * `plane_stack_index::UInt32`
  * `transform::SurfaceTransformFlagKHR`
  * `global_alpha::Float32`
  * `alpha_mode::DisplayPlaneAlphaFlagKHR`
  * `image_extent::Extent2D`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayPlaneSurfaceKHR.html)

```julia
create_display_plane_surface_khr(
    instance,
    display_mode,
    plane_index::Integer,
    plane_stack_index::Integer,
    transform::Vulkan.SurfaceTransformFlagKHR,
    global_alpha::Real,
    alpha_mode::Vulkan.DisplayPlaneAlphaFlagKHR,
    image_extent::Vulkan.Extent2D;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
