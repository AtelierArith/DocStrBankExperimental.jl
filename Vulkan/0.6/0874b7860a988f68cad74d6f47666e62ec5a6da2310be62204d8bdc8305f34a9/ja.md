拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `acquire_info::_PerformanceConfigurationAcquireInfoINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquirePerformanceConfigurationINTEL.html)

```julia
_acquire_performance_configuration_intel(
    device,
    acquire_info::Vulkan._PerformanceConfigurationAcquireInfoINTEL
) -> ResultTypes.Result{Vulkan.PerformanceConfigurationINTEL, Vulkan.VulkanError}

```
