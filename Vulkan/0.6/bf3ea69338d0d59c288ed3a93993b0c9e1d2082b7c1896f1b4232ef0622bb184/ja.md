拡張機能: VK*KHR*surface

引数:

  * `instance::Instance`
  * `surface::SurfaceKHR` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroySurfaceKHR.html)

```julia
destroy_surface_khr(instance, surface; allocator)

```
