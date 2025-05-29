拡張: VK*KHR*swapchain

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceGroupPresentCapabilitiesKHR.html)

```julia
_get_device_group_present_capabilities_khr(
    device
) -> ResultTypes.Result{Vulkan._DeviceGroupPresentCapabilitiesKHR, Vulkan.VulkanError}

```
