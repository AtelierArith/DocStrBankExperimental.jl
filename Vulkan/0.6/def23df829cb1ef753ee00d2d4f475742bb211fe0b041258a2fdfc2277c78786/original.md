Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `device::Device`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDeviceWaitIdle.html)

```julia
device_wait_idle(
    device
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
