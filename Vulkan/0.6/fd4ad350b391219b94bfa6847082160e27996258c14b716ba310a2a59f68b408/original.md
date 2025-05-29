Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::_EventCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateEvent.html)

```julia
_create_event(
    device,
    create_info::Vulkan._EventCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.Event, Vulkan.VulkanError}

```
