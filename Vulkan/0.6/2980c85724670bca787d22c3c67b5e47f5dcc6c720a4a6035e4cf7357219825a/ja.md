戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `signal_info::SemaphoreSignalInfo`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkSignalSemaphore.html)

```julia
signal_semaphore(
    device,
    signal_info::Vulkan.SemaphoreSignalInfo
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
