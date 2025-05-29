Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `plane_index::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDisplayPlaneSupportedDisplaysKHR.html)

```julia
_get_display_plane_supported_displays_khr(
    physical_device,
    plane_index::Integer
) -> ResultTypes.Result{Vector{Vulkan.DisplayKHR}, Vulkan.VulkanError}

```
