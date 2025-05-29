Extension: VK_EXT_acquire_drm_display

Return codes:

  * `SUCCESS`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `drm_fd::Int32`
  * `connector_id::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDrmDisplayEXT.html)

```julia
get_drm_display_ext(
    physical_device,
    drm_fd::Integer,
    connector_id::Integer
) -> ResultTypes.Result{Vulkan.DisplayKHR, Vulkan.VulkanError}

```
