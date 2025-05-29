Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceDisplayPlanePropertiesKHR.html)

```julia
get_physical_device_display_plane_properties_khr(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.DisplayPlanePropertiesKHR}, Vulkan.VulkanError}

```
