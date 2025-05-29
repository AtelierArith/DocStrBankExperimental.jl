Extension: VK_KHR_get_surface_capabilities2

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `physical_device::PhysicalDevice`
  * `surface_info::PhysicalDeviceSurfaceInfo2KHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceFormats2KHR.html)

```julia
get_physical_device_surface_formats_2_khr(
    physical_device,
    surface_info::Vulkan.PhysicalDeviceSurfaceInfo2KHR
) -> ResultTypes.Result{Vector{Vulkan.SurfaceFormat2KHR}, Vulkan.VulkanError}

```
