返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `device::Device`
  * `semaphore::Semaphore`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetSemaphoreCounterValue.html)

```julia
get_semaphore_counter_value(
    device,
    semaphore
) -> ResultTypes.Result{UInt64, Vulkan.VulkanError}

```
