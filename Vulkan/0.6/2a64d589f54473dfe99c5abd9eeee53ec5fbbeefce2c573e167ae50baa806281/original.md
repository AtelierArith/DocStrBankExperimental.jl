Extension: VK_KHR_get_display_properties2

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `display_plane_info::DisplayPlaneInfo2KHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayPlaneCapabilities2KHR.html)

```julia
get_display_plane_capabilities_2_khr(
    physical_device,
    display_plane_info::Vulkan.DisplayPlaneInfo2KHR
) -> ResultTypes.Result{Vulkan.DisplayPlaneCapabilities2KHR, Vulkan.VulkanError}

```
