拡張機能: VK*INTEL*performance_query

戻り値コード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `initialize_info::InitializePerformanceApiInfoINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkInitializePerformanceApiINTEL.html)

```julia
initialize_performance_api_intel(
    device,
    initialize_info::Vulkan.InitializePerformanceApiInfoINTEL
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
