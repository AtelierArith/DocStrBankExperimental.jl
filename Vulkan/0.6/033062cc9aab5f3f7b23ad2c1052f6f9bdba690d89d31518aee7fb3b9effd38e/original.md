Extension: VK_EXT_display_control

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `device_event_info::DeviceEventInfoEXT`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkRegisterDeviceEventEXT.html)

```julia
register_device_event_ext(
    device,
    device_event_info::Vulkan.DeviceEventInfoEXT;
    allocator
) -> ResultTypes.Result{Vulkan.Fence, Vulkan.VulkanError}

```
