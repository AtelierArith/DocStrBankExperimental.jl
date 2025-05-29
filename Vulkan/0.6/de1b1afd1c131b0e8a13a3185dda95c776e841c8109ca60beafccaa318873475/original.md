Extension: VK_KHR_get_display_properties2

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceDisplayProperties2KHR.html)

```julia
get_physical_device_display_properties_2_khr(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.DisplayProperties2KHR}, Vulkan.VulkanError}

```
