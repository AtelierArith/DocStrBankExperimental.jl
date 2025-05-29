Extension: VK_INTEL_performance_query

Return codes:

  * `SUCCESS`
  * `ERROR_TOO_MANY_OBJECTS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `configuration::PerformanceConfigurationINTEL`: defaults to `C_NULL` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkReleasePerformanceConfigurationINTEL.html)

```julia
_release_performance_configuration_intel(
    device;
    configuration
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
