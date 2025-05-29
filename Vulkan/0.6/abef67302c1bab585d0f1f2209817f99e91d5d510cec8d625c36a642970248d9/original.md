Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceGroupPresentCapabilitiesKHR.html)

```julia
_get_device_group_present_capabilities_khr(
    device
) -> ResultTypes.Result{Vulkan._DeviceGroupPresentCapabilitiesKHR, Vulkan.VulkanError}

```
