Extension: VK_EXT_display_control

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `display::DisplayKHR`
  * `display_event_info::DisplayEventInfoEXT`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkRegisterDisplayEventEXT.html)

```julia
register_display_event_ext(
    device,
    display,
    display_event_info::Vulkan.DisplayEventInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.Fence, Vulkan.VulkanError}

```
