Extension: VK_INTEL_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `parameter::PerformanceParameterTypeINTEL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPerformanceParameterINTEL.html)

```julia
get_performance_parameter_intel(
    device,
    parameter::Vulkan.PerformanceParameterTypeINTEL
) -> ResultTypes.Result{Vulkan.PerformanceValueINTEL, Vulkan.VulkanError}

```
