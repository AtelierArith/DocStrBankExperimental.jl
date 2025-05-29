Extension: VK_KHR_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`

Arguments:

  * `physical_device::PhysicalDevice`
  * `queue_family_index::UInt32`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkEnumeratePhysicalDeviceQueueFamilyPerformanceQueryCountersKHR.html)

```julia
enumerate_physical_device_queue_family_performance_query_counters_khr(
    physical_device,
    queue_family_index::Integer
) -> ResultTypes.Result{Tuple{Vector{Vulkan._PerformanceCounterKHR}, Vector{Vulkan._PerformanceCounterDescriptionKHR}}, Vulkan.VulkanError}

```
