拡張機能: VK*KHR*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

引数:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumeratePhysicalDeviceQueueFamilyPerformanceQueryCountersKHR.html)

```julia
_enumerate_physical_device_queue_family_performance_query_counters_khr(
    physical_device,
    queue_family_index::Integer
) -> ResultTypes.Result{Tuple{Vector{Vulkan._PerformanceCounterKHR}, Vector{Vulkan._PerformanceCounterDescriptionKHR}}, Vulkan.VulkanError}

```
