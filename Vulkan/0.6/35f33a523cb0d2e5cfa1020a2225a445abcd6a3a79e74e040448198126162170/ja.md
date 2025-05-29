拡張: VK*KHR*wayland_surface

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `instance::Instance`
  * `display::Ptr{wl_display}`
  * `surface::SurfaceKHR`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateWaylandSurfaceKHR.html)

```julia
_create_wayland_surface_khr(
    instance,
    display::Ptr{Nothing},
    surface::Ptr{Nothing};
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
