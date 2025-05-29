拡張: VK*KHR*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `TIMEOUT`

引数:

  * `device::Device`
  * `info::AcquireProfilingLockInfoKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireProfilingLockKHR.html)

```julia
acquire_profiling_lock_khr(
    device,
    info::Vulkan.AcquireProfilingLockInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
