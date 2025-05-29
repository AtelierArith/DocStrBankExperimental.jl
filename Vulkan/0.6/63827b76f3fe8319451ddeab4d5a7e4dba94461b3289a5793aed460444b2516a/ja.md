拡張: VK*EXT*device_fault

戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeviceFaultInfoEXT.html)

```julia
get_device_fault_info_ext(
    device
) -> ResultTypes.Result{Tuple{Vulkan._DeviceFaultCountsEXT, Vulkan._DeviceFaultInfoEXT}, Vulkan.VulkanError}

```
