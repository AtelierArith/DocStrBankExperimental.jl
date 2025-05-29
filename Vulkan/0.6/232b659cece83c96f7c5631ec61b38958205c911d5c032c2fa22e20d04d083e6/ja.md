拡張: VK*NV*cooperative_matrix

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceCooperativeMatrixPropertiesNV.html)

```julia
get_physical_device_cooperative_matrix_properties_nv(
    physical_device
) -> ResultTypes.Result{Vector{Vulkan.CooperativeMatrixPropertiesNV}, Vulkan.VulkanError}

```
