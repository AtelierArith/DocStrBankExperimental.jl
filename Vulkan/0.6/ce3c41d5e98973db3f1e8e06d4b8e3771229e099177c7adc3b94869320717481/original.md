Extension: VK_KHR_get_display_properties2

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayModeProperties2KHR.html)

```julia
get_display_mode_properties_2_khr(
    physical_device,
    display
) -> ResultTypes.Result{Vector{Vulkan.DisplayModeProperties2KHR}, Vulkan.VulkanError}

```
