拡張: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `mode::DisplayModeKHR` (externsync)
  * `plane_index::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayPlaneCapabilitiesKHR.html)

```julia
_get_display_plane_capabilities_khr(
    physical_device,
    mode,
    plane_index::Integer
) -> ResultTypes.Result{Vulkan._DisplayPlaneCapabilitiesKHR, Vulkan.VulkanError}

```
