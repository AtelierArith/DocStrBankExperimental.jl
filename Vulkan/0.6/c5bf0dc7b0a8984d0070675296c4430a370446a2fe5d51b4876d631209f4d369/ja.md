拡張機能: VK*INTEL*performance_query

戻りコード:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `parameter::PerformanceParameterTypeINTEL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPerformanceParameterINTEL.html)

```julia
_get_performance_parameter_intel(
    device,
    parameter::Vulkan.PerformanceParameterTypeINTEL
) -> ResultTypes.Result{Vulkan._PerformanceValueINTEL, Vulkan.VulkanError}

```
