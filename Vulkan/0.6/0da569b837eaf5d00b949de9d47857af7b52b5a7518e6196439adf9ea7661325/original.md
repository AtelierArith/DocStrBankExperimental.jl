Extension: VK_KHR_surface

Arguments:

  * `instance::Instance`
  * `surface::SurfaceKHR` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySurfaceKHR.html)

```julia
_destroy_surface_khr(instance, surface; allocator)

```
