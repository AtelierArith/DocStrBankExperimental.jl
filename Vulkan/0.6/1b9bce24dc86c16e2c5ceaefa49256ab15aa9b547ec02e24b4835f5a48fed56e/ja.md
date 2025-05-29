拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `queue::Queue`
  * `configuration::PerformanceConfigurationINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkQueueSetPerformanceConfigurationINTEL.html)

```julia
_queue_set_performance_configuration_intel(
    queue,
    configuration
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
