Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

Arguments:

  * `device::Device`
  * `surface::SurfaceKHR` (externsync)
  * `modes::DeviceGroupPresentModeFlagKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceGroupSurfacePresentModesKHR.html)

```julia
_get_device_group_surface_present_modes_khr(
    device,
    surface,
    modes::Vulkan.DeviceGroupPresentModeFlagKHR
) -> ResultTypes.Result{Vulkan.DeviceGroupPresentModeFlagKHR, Vulkan.VulkanError}

```
