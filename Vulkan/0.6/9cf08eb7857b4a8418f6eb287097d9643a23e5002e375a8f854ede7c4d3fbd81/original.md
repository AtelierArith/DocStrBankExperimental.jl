Extension: VK_EXT_headless_surface

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `instance::Instance`
  * `create_info::_HeadlessSurfaceCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateHeadlessSurfaceEXT.html)

```julia
_create_headless_surface_ext(
    instance,
    create_info::Vulkan._HeadlessSurfaceCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
