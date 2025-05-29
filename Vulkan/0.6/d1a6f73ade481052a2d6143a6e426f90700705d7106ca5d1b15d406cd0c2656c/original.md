Extension: VK_KHR_surface

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `physical_device::PhysicalDevice`
  * `surface::SurfaceKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceCapabilitiesKHR.html)

```julia
get_physical_device_surface_capabilities_khr(
    physical_device,
    surface
) -> ResultTypes.Result{Vulkan.SurfaceCapabilitiesKHR, Vulkan.VulkanError}

```
