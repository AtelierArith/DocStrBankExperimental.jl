Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `mode::DisplayModeKHR` (externsync)
  * `plane_index::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayPlaneCapabilitiesKHR.html)

```julia
_get_display_plane_capabilities_khr(
    physical_device,
    mode,
    plane_index::Integer
) -> ResultTypes.Result{Vulkan._DisplayPlaneCapabilitiesKHR, Vulkan.VulkanError}

```
