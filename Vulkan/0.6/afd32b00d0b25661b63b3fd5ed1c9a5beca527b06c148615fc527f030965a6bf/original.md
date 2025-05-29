Extension: VK_KHR_xlib_surface

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `instance::Instance`
  * `create_info::_XlibSurfaceCreateInfoKHR`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateXlibSurfaceKHR.html)

```julia
_create_xlib_surface_khr(
    instance,
    create_info::Vulkan._XlibSurfaceCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
