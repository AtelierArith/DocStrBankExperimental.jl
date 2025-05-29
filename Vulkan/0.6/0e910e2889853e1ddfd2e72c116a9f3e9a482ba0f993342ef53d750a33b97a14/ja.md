拡張: VK*KHR*fragment*shading*rate

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `physical_device::PhysicalDevice`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceFragmentShadingRatesKHR.html)

```julia
get_physical_device_fragment_shading_rates_khr(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.PhysicalDeviceFragmentShadingRateKHR}, Vulkan.VulkanError}

```
