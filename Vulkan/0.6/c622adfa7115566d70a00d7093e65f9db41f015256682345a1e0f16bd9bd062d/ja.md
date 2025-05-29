拡張: VK*KHR*surface

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`
  * `surface::SurfaceKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceSupportKHR.html)

```julia
get_physical_device_surface_support_khr(
    physical_device,
    queue_family_index::Integer,
    surface
) -> ResultTypes.Result{Bool, Vulkan.VulkanError}

```
