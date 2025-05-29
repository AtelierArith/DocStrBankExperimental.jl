Extension: VK_KHR_surface

Arguments:

  * `instance::Instance`
  * `surface::SurfaceKHR` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySurfaceKHR.html)

```julia
destroy_surface_khr(instance, surface; allocator)

```
