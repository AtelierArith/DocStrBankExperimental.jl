Extension: VK_INTEL_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `acquire_info::PerformanceConfigurationAcquireInfoINTEL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAcquirePerformanceConfigurationINTEL.html)

```julia
acquire_performance_configuration_intel(
    device,
    acquire_info::Vulkan.PerformanceConfigurationAcquireInfoINTEL
) -> ResultTypes.Result{Vulkan.PerformanceConfigurationINTEL, Vulkan.VulkanError}

```
