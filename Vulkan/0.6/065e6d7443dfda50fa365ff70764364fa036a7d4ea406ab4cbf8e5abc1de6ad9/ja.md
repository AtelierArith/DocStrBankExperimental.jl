拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `configuration::PerformanceConfigurationINTEL`: デフォルトは `C_NULL` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkReleasePerformanceConfigurationINTEL.html)

```julia
release_performance_configuration_intel(
    device;
    configuration
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
