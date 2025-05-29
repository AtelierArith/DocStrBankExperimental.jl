Extension: VK_EXT_acquire_drm_display

Return codes:

  * `SUCCESS`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `physical_device::PhysicalDevice`
  * `drm_fd::Int32`
  * `display::DisplayKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireDrmDisplayEXT.html)

```julia
_acquire_drm_display_ext(
    physical_device,
    drm_fd::Integer,
    display
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
