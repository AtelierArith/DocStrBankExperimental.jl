拡張: VK*KHR*display

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayModePropertiesKHR.html)

```julia
_get_display_mode_properties_khr(
    physical_device,
    display
) -> ResultTypes.Result{Vector{Vulkan._DisplayModePropertiesKHR}, Vulkan.VulkanError}

```
