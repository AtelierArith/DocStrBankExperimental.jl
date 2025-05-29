Extension: VK_KHR_swapchain

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `physical_device::PhysicalDevice`
  * `surface::SurfaceKHR` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetPhysicalDevicePresentRectanglesKHR.html)

```julia
get_physical_device_present_rectangles_khr(
    physical_device,
    surface
) -> ResultTypes.Result{Vector{Vulkan.Rect2D}, Vulkan.VulkanError}

```
