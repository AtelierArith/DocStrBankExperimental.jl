拡張: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `instance::Instance`
  * `create_info::DisplaySurfaceCreateInfoKHR`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayPlaneSurfaceKHR.html)

```julia
create_display_plane_surface_khr(
    instance,
    create_info::Vulkan.DisplaySurfaceCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
