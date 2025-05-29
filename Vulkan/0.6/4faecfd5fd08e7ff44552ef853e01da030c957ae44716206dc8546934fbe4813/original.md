Return codes:

  * `EVENT_SET`
  * `EVENT_RESET`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `device::Device`
  * `event::Event`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetEventStatus.html)

```julia
get_event_status(
    device,
    event
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
