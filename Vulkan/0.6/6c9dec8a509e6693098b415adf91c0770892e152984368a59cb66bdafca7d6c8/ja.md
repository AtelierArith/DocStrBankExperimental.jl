拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `initialize_info::_InitializePerformanceApiInfoINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkInitializePerformanceApiINTEL.html)

```julia
_initialize_performance_api_intel(
    device,
    initialize_info::Vulkan._InitializePerformanceApiInfoINTEL
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
