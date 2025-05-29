Extension: VK_EXT_device_fault

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceFaultInfoEXT.html)

```julia
_get_device_fault_info_ext(
    device
) -> ResultTypes.Result{Tuple{Vulkan._DeviceFaultCountsEXT, Vulkan._DeviceFaultInfoEXT}, Vulkan.VulkanError}

```
