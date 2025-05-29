Extension: VK_INTEL_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `queue::Queue`
  * `configuration::PerformanceConfigurationINTEL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueueSetPerformanceConfigurationINTEL.html)

```julia
_queue_set_performance_configuration_intel(
    queue,
    configuration
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
