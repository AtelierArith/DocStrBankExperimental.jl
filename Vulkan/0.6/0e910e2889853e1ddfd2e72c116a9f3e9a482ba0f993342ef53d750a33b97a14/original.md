Extension: VK_KHR_fragment_shading_rate

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceFragmentShadingRatesKHR.html)

```julia
get_physical_device_fragment_shading_rates_khr(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.PhysicalDeviceFragmentShadingRateKHR}, Vulkan.VulkanError}

```
