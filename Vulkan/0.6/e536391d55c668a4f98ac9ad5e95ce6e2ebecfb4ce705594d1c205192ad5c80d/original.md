Extension: VK_KHR_display

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `physical_device::PhysicalDevice`
  * `display::DisplayKHR` (externsync)
  * `parameters::DisplayModeParametersKHR`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDisplayModeKHR.html)

```julia
create_display_mode_khr(
    physical_device,
    display,
    parameters::Vulkan.DisplayModeParametersKHR;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.DisplayModeKHR, Vulkan.VulkanError}

```
