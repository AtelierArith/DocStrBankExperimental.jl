拡張機能: VK*KHR*get*display*properties2

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayModeProperties2KHR.html)

```julia
get_display_mode_properties_2_khr(
    physical_device,
    display
) -> ResultTypes.Result{Vector{Vulkan.DisplayModeProperties2KHR}, Vulkan.VulkanError}

```
