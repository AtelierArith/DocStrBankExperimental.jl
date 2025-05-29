Extension: VK_INTEL_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `initialize_info::InitializePerformanceApiInfoINTEL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkInitializePerformanceApiINTEL.html)

```julia
initialize_performance_api_intel(
    device,
    initialize_info::Vulkan.InitializePerformanceApiInfoINTEL
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
