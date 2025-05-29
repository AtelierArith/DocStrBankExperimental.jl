Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayModePropertiesKHR.html)

```julia
get_display_mode_properties_khr(
    physical_device,
    display
) -> ResultTypes.Result{Vector{Vulkan.DisplayModePropertiesKHR}, Vulkan.VulkanError}

```
