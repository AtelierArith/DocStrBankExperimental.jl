拡張: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceDisplayPropertiesKHR.html)

```julia
_get_physical_device_display_properties_khr(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan._DisplayPropertiesKHR}, Vulkan.VulkanError}

```
