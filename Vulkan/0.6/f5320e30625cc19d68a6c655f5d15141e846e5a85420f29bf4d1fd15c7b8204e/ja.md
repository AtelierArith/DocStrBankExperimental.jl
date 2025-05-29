拡張機能: VK*KHR*get*display*properties2

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `display_plane_info::_DisplayPlaneInfo2KHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayPlaneCapabilities2KHR.html)

```julia
_get_display_plane_capabilities_2_khr(
    physical_device,
    display_plane_info::Vulkan._DisplayPlaneInfo2KHR
) -> ResultTypes.Result{Vulkan._DisplayPlaneCapabilities2KHR, Vulkan.VulkanError}

```
