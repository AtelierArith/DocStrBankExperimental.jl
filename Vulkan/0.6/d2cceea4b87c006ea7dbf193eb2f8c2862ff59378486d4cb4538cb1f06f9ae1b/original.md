Extension: VK_KHR_xlib_surface

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `instance::Instance`
  * `dpy::Ptr{Display}`
  * `window::Window`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateXlibSurfaceKHR.html)

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
