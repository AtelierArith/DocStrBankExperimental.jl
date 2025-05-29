Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `create_info::DisplayModeCreateInfoKHR`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

```julia
create_display_mode_khr(
    physical_device,
    display,
    create_info::Vulkan.DisplayModeCreateInfoKHR;
    allocator
) -> ResultTypes.Result{Vulkan.DisplayModeKHR, Vulkan.VulkanError}

```
