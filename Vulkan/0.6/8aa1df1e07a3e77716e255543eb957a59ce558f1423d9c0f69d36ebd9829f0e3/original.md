Extension: VK_KHR_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `TIMEOUT`

Arguments:

  * `device::Device`
  * `info::AcquireProfilingLockInfoKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquireProfilingLockKHR.html)

```julia
acquire_profiling_lock_khr(
    device,
    info::Vulkan.AcquireProfilingLockInfoKHR
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
