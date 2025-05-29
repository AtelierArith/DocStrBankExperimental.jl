拡張: VK*KHR*surface

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `physical_device::PhysicalDevice`
  * `surface::SurfaceKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceFormatsKHR.html)

```julia
_get_physical_device_surface_formats_khr(
    physical_device;
    surface
) -> ResultTypes.Result{Vector{Vulkan._SurfaceFormatKHR}, Vulkan.VulkanError}

```
