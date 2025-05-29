拡張: VK*KHR*swapchain

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `device::Device`
  * `surface::SurfaceKHR` (externsync)
  * `modes::DeviceGroupPresentModeFlagKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceGroupSurfacePresentModesKHR.html)

```julia
get_device_group_surface_present_modes_khr(
    device,
    surface,
    modes::Vulkan.DeviceGroupPresentModeFlagKHR
) -> ResultTypes.Result{Vulkan.DeviceGroupPresentModeFlagKHR, Vulkan.VulkanError}

```
