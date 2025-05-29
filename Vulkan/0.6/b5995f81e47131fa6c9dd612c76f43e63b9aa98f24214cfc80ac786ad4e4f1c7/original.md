Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `event::Event` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSetEvent.html)

```julia
_set_event(
    device,
    event
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
