拡張: VK*EXT*headless_surface

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `instance::Instance`
  * `create_info::_HeadlessSurfaceCreateInfoEXT`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateHeadlessSurfaceEXT.html)

```julia
_create_headless_surface_ext(
    instance,
    create_info::Vulkan._HeadlessSurfaceCreateInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.SurfaceKHR, Vulkan.VulkanError}

```
