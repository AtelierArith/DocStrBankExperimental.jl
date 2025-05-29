拡張: VK*KHR*get*surface*capabilities2

戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `physical_device::PhysicalDevice`
  * `surface_info::_PhysicalDeviceSurfaceInfo2KHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceFormats2KHR.html)

```julia
_get_physical_device_surface_formats_2_khr(
    physical_device,
    surface_info::Vulkan._PhysicalDeviceSurfaceInfo2KHR
) -> ResultTypes.Result{Vector{Vulkan._SurfaceFormat2KHR}, Vulkan.VulkanError}

```
