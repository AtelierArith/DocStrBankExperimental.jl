拡張: VK*KHR*swapchain

戻り値コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `physical_device::PhysicalDevice`
  * `surface::SurfaceKHR` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDevicePresentRectanglesKHR.html)

```julia
_get_physical_device_present_rectangles_khr(
    physical_device,
    surface
) -> ResultTypes.Result{Vector{Vulkan._Rect2D}, Vulkan.VulkanError}

```
