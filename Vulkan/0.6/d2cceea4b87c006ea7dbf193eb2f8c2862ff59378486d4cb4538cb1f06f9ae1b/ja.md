拡張: VK*KHR*xlib_surface

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `instance::Instance`
  * `dpy::Ptr{Display}`
  * `window::Window`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateXlibSurfaceKHR.html)

```julia
create_xlib_surface_khr(
    instance,
    dpy::Ptr{Nothing},
    window::UInt64;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
