拡張: VK*KHR*get*surface*capabilities2

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_SURFACE_LOST_KHR`

引数:

  * `physical_device::PhysicalDevice`
  * `surface_info::PhysicalDeviceSurfaceInfo2KHR`
  * `next_types::Type...`: `next` チェーンの一部として初期化し、含めるメンバーの型

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDeviceSurfaceCapabilities2KHR.html)

```julia
get_physical_device_surface_capabilities_2_khr(
    physical_device,
    surface_info::Vulkan.PhysicalDeviceSurfaceInfo2KHR,
    next_types::Type...
) -> ResultTypes.Result{Vulkan.SurfaceCapabilities2KHR, Vulkan.VulkanError}

```
