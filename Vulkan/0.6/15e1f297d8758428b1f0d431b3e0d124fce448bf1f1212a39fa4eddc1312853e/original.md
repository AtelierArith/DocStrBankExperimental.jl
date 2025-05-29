Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `signal_info::_SemaphoreSignalInfo`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSignalSemaphore.html)

```julia
_signal_semaphore(
    device,
    signal_info::Vulkan._SemaphoreSignalInfo
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
