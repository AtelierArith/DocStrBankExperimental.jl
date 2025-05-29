Extension: VK_EXT_calibrated_timestamps

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceCalibrateableTimeDomainsEXT.html)

```julia
get_physical_device_calibrateable_time_domains_ext(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.TimeDomainEXT}, Vulkan.VulkanError}

```
