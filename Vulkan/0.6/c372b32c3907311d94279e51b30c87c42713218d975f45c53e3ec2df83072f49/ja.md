拡張機能: VK*EXT*calibrated_timestamps

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceCalibrateableTimeDomainsEXT.html)

```julia
_get_physical_device_calibrateable_time_domains_ext(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.TimeDomainEXT}, Vulkan.VulkanError}

```
