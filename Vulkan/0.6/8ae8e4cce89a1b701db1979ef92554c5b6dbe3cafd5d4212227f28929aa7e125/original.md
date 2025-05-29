Extension: VK_KHR_get_surface_capabilities2

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `physical_device::PhysicalDevice`
  * `surface_info::_PhysicalDeviceSurfaceInfo2KHR`
  * `next_types::Type...`: types of members to initialize and include as part of the `next` chain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceCapabilities2KHR.html)

```julia
_get_physical_device_surface_capabilities_2_khr(
    physical_device,
    surface_info::Vulkan._PhysicalDeviceSurfaceInfo2KHR,
    next_types::Type...
) -> ResultTypes.Result{Vulkan._SurfaceCapabilities2KHR, Vulkan.VulkanError}

```
