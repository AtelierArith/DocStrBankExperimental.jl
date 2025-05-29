Extension: VK_KHR_surface

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`
  * `surface::SurfaceKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceSupportKHR.html)

```julia
_get_physical_device_surface_support_khr(
    physical_device,
    queue_family_index::Integer,
    surface
) -> ResultTypes.Result{Bool, Vulkan.VulkanError}

```
