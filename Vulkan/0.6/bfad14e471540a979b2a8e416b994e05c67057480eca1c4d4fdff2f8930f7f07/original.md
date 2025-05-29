Return codes:

  * `SUCCESS`
  * `TIMEOUT`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `device::Device`
  * `wait_info::SemaphoreWaitInfo`
  * `timeout::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkWaitSemaphores.html)

```julia
wait_semaphores(
    device,
    wait_info::Vulkan.SemaphoreWaitInfo,
    timeout::Integer
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
